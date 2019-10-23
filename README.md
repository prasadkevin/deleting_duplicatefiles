# deleting_duplicatefiles






import cv2
import numpy as np
import os, glob
import shutil
import time
import ntpath


def path_leaf(path):
    head, tail = ntpath.split(path)
    return tail or ntpath.basename(head)

duplicateFiles = glob.glob('all/temp/*')
allFiles = glob.glob('all/ATM_video/*')

duplicateFiles_noPath = []

for file in duplicateFiles:
    duplicateFiles_noPath.append(path_leaf(file))
    
allFiles_nopath = []
for file in allFiles:
    allFiles_nopath.append(path_leaf(file))
    
#for file in duplicateFiles_noPath:  
#    if file in allFiles_nopath:
#        os.remove('all/ATM_video/' + file)
        
commofiles = list(set(allFiles_nopath).intersection(duplicateFiles_noPath))   
for file in commofiles :
    os.remove('all/ATM_video/' + file)
