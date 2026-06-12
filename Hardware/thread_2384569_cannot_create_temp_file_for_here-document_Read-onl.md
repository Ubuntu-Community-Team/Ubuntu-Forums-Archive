---
title: "cannot create temp file for here-document: Read-only file system"
date: 2018-02-08
forum: Hardware
---

### Post by lp.descamps on 2018-02-08
hi

this happens very frequently.

the way to fix it is fsck and reboot

i m on ubuntu 17.10.1
any idea?
this is a ssd and i m worried it&#347; faulty
thanks

```
lpdne@Vostro-17:~$ sudo fsck /dev/sda6 -y
[sudo] password for lpdne: 
fsck from util-linux 2.30.1
e2fsck 1.43.5 (04-Aug-2017)
/dev/sda6: recovering journal
/dev/sda6 contains a filesystem with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix? yes

Inode 393219 was part of the orphaned inode list.  FIXED.
Inode 393220 was part of the orphaned inode list.  FIXED.
Inode 393221 was part of the orphaned inode list.  FIXED.
Inode 393222 was part of the orphaned inode list.  FIXED.
Inode 393223 was part of the orphaned inode list.  FIXED.
Inode 393226 was part of the orphaned inode list.  FIXED.
Inode 393227 was part of the orphaned inode list.  FIXED.
Inode 393229 was part of the orphaned inode list.  FIXED.
Inode 393230 was part of the orphaned inode list.  FIXED.
Inode 393231 was part of the orphaned inode list.  FIXED.
Inode 393233 was part of the orphaned inode list.  FIXED.
Inode 1311202 was part of the orphaned inode list.  FIXED.
Inode 1311203 was part of the orphaned inode list.  FIXED.
Inode 12191842 was part of the orphaned inode list.  FIXED.
Inode 12191843 was part of the orphaned inode list.  FIXED.
Inode 14683926 was part of the orphaned inode list.  FIXED.
Inode 14683927 was part of the orphaned inode list.  FIXED.
Inode 14683929 was part of the orphaned inode list.  FIXED.
Inode 14683934 was part of the orphaned inode list.  FIXED.
Inode 14683935 was part of the orphaned inode list.  FIXED.
Inode 14683936 was part of the orphaned inode list.  FIXED.
Inode 14683941 was part of the orphaned inode list.  FIXED.
Inode 14683944 was part of the orphaned inode list.  FIXED.
Inode 14683952 was part of the orphaned inode list.  FIXED.
Inode 14683954 was part of the orphaned inode list.  FIXED.
Inode 14683955 was part of the orphaned inode list.  FIXED.
Inode 14683956 was part of the orphaned inode list.  FIXED.
Inode 14683957 was part of the orphaned inode list.  FIXED.
Inode 14683958 was part of the orphaned inode list.  FIXED.
Inode 14684009 was part of the orphaned inode list.  FIXED.
Deleted inode 15728672 has zero dtime.  Fix? yes

Inode 15728673 was part of the orphaned inode list.  FIXED.
Inode 22020612 extent tree (at level 1) could be shorter.  Fix? yes

Inode 22020612, i_blocks is 2264, should be 8.  Fix? yes

Inode 22021501 was part of the orphaned inode list.  FIXED.
Inode 22031629 was part of the orphaned inode list.  FIXED.
Inode 27792546 was part of the orphaned inode list.  FIXED.
Inode 28192378 was part of the orphaned inode list.  FIXED.
Pass 1E: Optimising extent trees
Failed to optimise extent tree <22020612> (22020612): Extent not found
Pass 2: Checking directory structure
Directory inode 22020253, block #0: directory passes checks but fails checksum.
Fix? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(624455--624502) -(1084946--1084951) -(1949448--1949453) -(1949465--1949474) -(38883889--38883894) -48791002 -(48962789--48962794) -(48978022--48978024) -(48984457--48984462) -(48985990--48985996) -(49015983--49015988) -(56014848--56016897) -(57111040--57111595) -(59351040--59353087) -(59398144--59400191) -(59447296--59449343) -(59478016--59480063) -(59512832--59514879) -(59520274--59521449) -(61113216--61113310) -(61125632--61126235) -(61126656--61127087) -(61127168--61127797) -(61128704--61159235) -(61159296--61159401) -(61159424--61162427) -(61162432--61162485) -(61162496--61162690) -(61163008--61163872) -(61164032--61164289) -(61164544--61168051) -(61168128--61168459) -(61168640--61169305) -(61173632--61173683) -(62951429--62951434) -(62951444--62951457) -(62951469--62951474) -88113163 -(88312350--88312355) -(88312376--88312381) -(88312385--88312390) -(88317981--88317986) -(88317995--88318008)
Fix? yes

Free blocks count wrong for group #19 (8734, counted=8782).
Fix? yes

Free blocks count wrong for group #33 (1921, counted=1927).
Fix? yes

Free blocks count wrong for group #48 (946, counted=1225).
Fix? yes

Free blocks count wrong for group #59 (1543, counted=1559).
Fix? yes

Free blocks count wrong for group #1186 (1051, counted=1057).
Fix? yes

Free blocks count wrong for group #1488 (8734, counted=8735).
Fix? yes

Free blocks count wrong for group #1494 (21602, counted=21624).
Fix? yes

Free blocks count wrong for group #1495 (15503, counted=15509).
Fix? yes

Free blocks count wrong for group #1709 (2046, counted=4096).
Fix? yes

Free blocks count wrong for group #1742 (6685, counted=7241).
Fix? yes

Free blocks count wrong for group #1811 (0, counted=2048).
Fix? yes

Free blocks count wrong for group #1812 (0, counted=2048).
Fix? yes

Free blocks count wrong for group #1814 (0, counted=2048).
Fix? yes

Free blocks count wrong for group #1815 (0, counted=2048).
Fix? yes

Free blocks count wrong for group #1816 (4400, counted=7624).
Fix? yes

Free blocks count wrong for group #1865 (14623, counted=32768).
Fix? yes

Free blocks count wrong for group #1866 (9499, counted=32687).
Fix? yes

Free blocks count wrong for group #1921 (26638, counted=26664).
Fix? yes

Free blocks count wrong for group #2689 (14153, counted=14154).
Fix? yes

Free blocks count wrong for group #2695 (15221, counted=15259).
Fix? yes

Free blocks count wrong (34012220, counted=33156258).
Fix? yes

Inode bitmap differences:  -(393219--393223) -(393226--393227) -(393229--393231) -393233 -(1311202--1311203) -(12191842--12191843) -(14683926--14683927) -14683929 -(14683934--14683936) -14683941 -14683944 -14683952 -(14683954--14683958) -14684009 -(15728672--15728673) -22021501 -22031629 -27792546 -28192378
Fix? yes

Free inodes count wrong for group #48 (8145, counted=8156).
Fix? yes

Free inodes count wrong for group #160 (7599, counted=7601).
Fix? yes

Free inodes count wrong for group #1488 (5360, counted=5362).
Fix? yes

Directories count wrong for group #1488 (726, counted=725).
Fix? yes

Free inodes count wrong for group #1792 (4319, counted=4334).
Fix? yes

Free inodes count wrong for group #1920 (8089, counted=8091).
Fix? yes

Free inodes count wrong for group #2688 (0, counted=1).
Fix? yes

Free inodes count wrong for group #2689 (3960, counted=3961).
Fix? yes

Free inodes count wrong for group #3392 (2808, counted=2809).
Fix? yes

Free inodes count wrong for group #3441 (3707, counted=3708).
Fix? yes

Free inodes count wrong (28492340, counted=28489216).
Fix? yes


/dev/sda6: ***** FILESYSTEM WAS MODIFIED *****
/dev/sda6: ***** REBOOT SYSTEM *****
/dev/sda6: 502272/28991488 files (2.1% non-contiguous), 82784606/115940864 blocks

```

---

### Post by TheFu on 2018-02-09
fsck can't fix every error.  Eventually, you'll have problems.  Find the root cause.

Check
* cables.
* controller.
* power supply.
* corrupted programs - a fresh install AFTER you've fixed the other issues would be best.
* for storage, check the device SMART data. Any issues there?

---

