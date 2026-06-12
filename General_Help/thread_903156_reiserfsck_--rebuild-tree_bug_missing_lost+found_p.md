---
title: "reiserfsck --rebuild-tree bug missing lost+found please help"
date: 2008-08-28
forum: General Help
---

### Post by tkanter on 2008-08-28
Please help! Reiserfs on an LVM volume did not respond well to a power outage. The real problem is that reiserfsck --rebuild-tree just failes due to a known bug (missing lost+found) for which I was unable to find a fix, which some posts on the Internet mentioned exist, but the namesys.com site does not respond. Below you find the output from reiserfsck (minus the log file with detected error corrections). This server is running Hardy. 

--theo


# sudo reiserfsck --scan-whole-partition --rebuild-tree --logfile /home/theo/rfsck.log.1 /dev/mapper/vgWARP-lvDRIVE 
reiserfsck 3.6.19 (2003 [www.namesys.com](www.namesys.com))

[..reiserfsck general disclaimer cut out..]

Will rebuild the filesystem (/dev/mapper/vgWARP-lvDRIVE) tree
Will put log info to '/home/theo/rfsck.log.1'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
Replaying journal..
Reiserfs journal '/dev/mapper/vgWARP-lvDRIVE' in blocks [18..8211]: 0 transactions replayed
###########
reiserfsck --rebuild-tree started at Wed Aug 27 21:05:01 2008
###########

Pass 0:
The whole partition (245815296 blocks) is to be scanned
Skipping 15712 blocks (super block, journal, bitmaps) 245799584 blocks will be read
0%....                                                        left 0, 13274 /secccc
	"r5" hash is selected
Flushing..finished
	Read blocks (but not data blocks) 245799584
		Leaves among those 431089
			- corrected leaves 163
			- leaves all contents of which could not be saved and deleted 802
		Objectids found 281125

Pass 1 (will try to insert 430287 leaves):
Looking for allocable blocks .. finished
0%....20%....40%....60%....80%....100%                         left 0, 247 /sec
Flushing..finished
	430287 leaves read
		364527 inserted
			- pointers in indirect items pointing to metadata 54 (zeroed)
		65760 not inserted
	non-unique pointers in indirect items (zeroed) 2982713

Pass 2:
0%....20%....40%....60%....80%....100%                         left 0, 142 /sec
Flushing..finished
	Leaves inserted item by item 65760
Pass 3 (semantic):
Flushing..finished                                                             
	Files found: 104864
	Directories found: 10111
	Broken (of files/symlinks/others): 3
	Files with fixed size: 1
	Names pointing to nowhere (removed): 404
	Objects having used objectids: 1
		files fixed 1
Pass 3a (looking for lost dir/files):
Looking for lost directories:
Looking for lost files:9 /sec                                                  
lost+found.c 348 pass_3a_look_for_lost
look_for_lost: The entry 'lost+found' could not be found in the root directory.
Aborted
#

---

