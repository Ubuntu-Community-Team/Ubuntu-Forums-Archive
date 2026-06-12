---
title: "Cannot install 7.10 on VIA EPIA EX10000EG"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by lytke on 2008-02-14
Setup:
Via Epia ex-10000EG
LCD monitor connected via DVI
USB keyboard and mouse

Problem:
When booting on UBUNTU CD it stops efter trying to load X a number of times.

Getting error message:
"The display server has been shut down about 6 times in the last 90 seconds.It is likely that something bad is going on. Waiting for 2 minutes before trying again on display:0."

Tried:
When switching to a virtual terminal (ctrl-alt-f4) and run "startx"  I get the following message "(EE) AIGLX: Screen 0 is not DRi capable"

Not able to install anything !

Any suggestions ?

---

### Post by tgalati4 on 2008-02-14
It could be as simple as the wrong refresh rate for your display.  Try booting with the "safe graphics" mode and see if it will come up.  If it does, then dig around for an old VGA monitor and use that to install it and set it up.  If successful, then you can play around with the display resolution and refresh rate.  You want to set the exact resolution for the LCD to get the best display.

Be mindful that the Epia boards use Via graphics chips and openchrome drivers are somewhat buggy.  Search openchrome in the forums for some clues.

---

### Post by lytke on 2008-02-15
Monitor Settings in BIOS changed from [ DVI + TV]  to  [DVI]

Try and try again, when error comes up, **run startx** from another session (ctrl-alt-F4) 
- now a picture comes up and installation can begin.......

Afterwards download and install driver from viaarena (specially compiled for UBUNTU 7.10)
- this looks good, nice clear steady picture appears.

Configure tv-card (Nova-t 500) and MythTV, looking really good, channel guide works, performance seems just fine.

Start viewing TV .......screen goes black, nothing, no contact :(

restart pc, looking for traces in logfiles

---

### Post by aidan_curtis on 2008-03-12
any luck since?

---

### Post by aidan_curtis on 2008-03-23
Ive built a box using a Via EX10000eg mother board and a hvr 4000 heres how 
1.  insert disk and boot pick default install option
2.  when Xserver fails type <CTRL>+<ALT>+<F4>
3.  at the $ prompt type startx<ENTER>
4.  follow the install proceedure
5.  Reboot
6.  when Xserver fails type <CTRL>+<ALT>+<F4>
7.  log in to the console using the username and password setup during the install
8.  at the $ prompt type startx<ENTER>
9.  do the system updates
10. reboot
11. when Xserver fails type <CTRL>+<ALT>+<F4>
12. log in to the console using the username and password setup during the install
13. at the $ prompt type startx<ENTER>
14. Add the restricted multivers and universe and backports and package lists to the distribution using Applications\System\Software Sources
15. run Applications\System\Update Manager, Install any updates
16. reboot.
17. when Xserver fails type <CTRL>+<ALT>+<F4>
18. log in to the console using the username and password setup during the install
19. at the $ prompt type startx<ENTER>
20. using Applications\System\Synaptic Package Manager add the libgl-mesa-dri package 
21. it might be wise to try removing xserver-xorg-video-via
22. sudo apt-get build-dep xserver-xorg-video-via
23. Create a directory src in your home directory
24. download and extract [http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip](http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip) to the src directory
25. open a terminal type cd src <ENTER>
26. type chmod 755 VIA_U710_UniChrome-GFX-v40072d.run <ENTER>
27. type sudo ./VIA_U710_UniChrome-GFX-v40072d.run <ENTER> and pick option 1.install
28  reboot and determine display resolution and set it using S3utility and Applications\Settings\Screens and Graplics
29. move the task list, show desktop and trash items from the pannel along the bottom of the screen to the panel at the top
30. remove everything else of the pannel bar along the bottom
31. change the number of workspaces to one using Applications\Settings\Workspace Settings
32. Set the pannel at the top of the screen to a width of 30 and set it's location to the bottom center of the screen using Applications\Settings\Panel Manager
33. reboot.
33a. using Applications\System\Software Sources remove backports
34. Install Filezilla,dvb-utils, rtorrent, mplayer, mplayer-doc, mplayer-fonts & mplayer-skins using using Applications\System\Synaptic Package Manager
35. sudo apt-get install mercurial.
36. hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
37. cd v4l-dvb
38. wget [http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff](http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff)
39. patch -p1 < v4l-dvb-hg-sfe-latest.diff
40. edit and fix any problems from previous act. look at the output you'll see which files didnt diff
41. make
42. sudo make install
43. wget [ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip](ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip)
44. decompress what's needed : "unzip -jo 88x_2_119_25023_WHQL.zip Driver88/hcw88bda.sys"
45. sudo dd if=hcw88bda.sys of=dvb-fe-cx24116.fw skip=81768 bs=1 count=32522
46. copy dvb-fe-cx24116.fw to /lib/firmware/2.6.22-14-generic
47. reboot
48. make sure that the xorg.conf is correct i.e. set keyboard to "ie" and Load	"dri" alernatively copy the xorg.conf from src.
49. to test tune mkdir .szap
50. scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E > ./.szap/channels.conf
51. run mplayer
52  cp ./.szap/channels.conf ./.mplayer/channels.conf
53. mplayer dvb://UTV
54. firefox to [http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu)
55. click install mythbuntu and select install packages /select haugauge nova t 500 as the lirc
56. reboot
57. run Applications\System\Mythbuntu Control Centre
58. click system roles
59. setup as primary backend and as frontend
60. reboot
61. run Applications\System\Mythbuntu Control Centre
62. click mythtv configuration
63. launch mythtv setup
64. answer yes to adding user to mythtv group and restart 
65. run Applications\System\Mythbuntu Control Centre
66. click mythtv configuration
67. launch mythtv setup setup inputs do channel scans etc
68. reboot
69. [http://www.nabble.com/MythTV-won't-run-with-VIA-CX700M2-chipset-td15040477s15552.html](http://www.nabble.com/MythTV-won't-run-with-VIA-CX700M2-chipset-td15040477s15552.html)
70. sudo apt-get install build-essential
71. sudo apt-get build-dep mythtv
72. cd src
73. apt-get source mythtv
74. In libs/mythtv/vsync.cpp, comment out the following line in VideoSyn::BestMethod (line 95): //TESTVIDEOSYNC(DRMVideoSync);
75. In libs/mythtv/videoout_xv.cpp, uncomment line 67: #define USE_ATI_PROPRIETARY_DRIVER_XVIDEO_HACK
76. ./configure --enable-dvb --enable-proc-opt --prefix=/usr --enable-xvmc --enable-xvmc-pro --enable-xvmc-vld
77.  qmake mythtv.pro
78. make
79. sudo make install
80. Applications\System\run myth-setup and after that try to run the frontend and reboot
81. run Applications\System\Mythbuntu Control Centre
82. click system roles
83. remove as primary backend and as frontend
84. run Applications\System\Mythbuntu Control Centre
85. click system roles
86. setup as primary backend and as frontend
87. launch frontend
88. reboot if required and relaunch frontend
89. setup settings (notice lack of skins)
90. run Applications\System\Mythbuntu Control Centre
91. click applications & plugins add em all.
92. reboot
93. run Applications\System\Mythbuntu Control Centre
94. click proprietary codecs enable medibuntu proprietary codec support apply
95. it appears that the changes dont finish just run the update manager beside the clock when you get sick waiting.
96. reboot
97. run Applications\System\Mythbuntu Control Centre
98. click proprietary codecs all the available codecs
99. Install the mythtv-themes using Applications\System\Synaptic Package Manager do a search you'll find them.
100. reboot
101. rerun frontend and pick the right theme you will probably have to rerun it a couple of times
102. run Applications\System\Mythbuntu Control Centre
103. click system services enable mysql service and apply
104. click system services enable vnc service , set password and apply
105. click system services enable ssh services and apply
106. reboot
107. run Applications\System\Mythbuntu Control Centre
108. click artwork and login behavour, enable automatic login 
109. reboot 
110. you may  have to edit xorg.conf again.
111. there are are some problems with mythbuntu the links in /www/mythweb/data/ they are pointing to the wrong places fix as follows
112. cd /var/www/mythweb/data
113. sudo rm ./video_covers
114. sudo rm ./video
115. sudo ln -s /var/lib/mythtv/videos ./video
116. sudo ln -s /var/lib/mythtv/videos ./video_covers
117. cd /var/www/mythweb
118. sudo chown root:www-data ./data
119. sudo chmod +t /usr/share/mythtv/mythweb/data (thanks Gary Parker "http://www.parker1.co.uk/mythtv_0.20.php")
120. add www-data to the mythtv group in /etc/group.
120. Install Webmin its a damm good way of managing the box. (personal opinion)
121. the remote control needs some work  again one should have a look at [http://www.parker1.co.uk/mythtv_tips.php](http://www.parker1.co.uk/mythtv_tips.php)
122. use this to back up the disk [http://ping.windowsdream.com/](http://ping.windowsdream.com/)

Thanks to all at the ubuntu forums, lytke, Billdozer, Darron Broad, Menthol, Garry Parker, Eugene Gargan and lots of others
Hope this helps someone else.
Aidan

---

