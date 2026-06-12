---
title: "CUPS problem?  Ubuntu thinks the printer is still out of ink..."
date: 2011-11-01
forum: Hardware
---

### Post by Superluke on 2011-11-01
Ubuntu 11.10 64-bit.

My printer is a Brother MFC-440CN, and it's always worked perfectly with Ubuntu, until now - we put a new black ink cartridge in it, it worked fine, and then suddenly Ubuntu decided that it's out of ink again.  The printer's display shows full black, so the intormation isn't coming from there.  Is there any way to force CUPS to reset the values so I can print???  


HELP!

Edit - I tried removing the printer and reinstalling, and it's lost the driver altogether.  It's still in the system but can't be found automatically.  Also this happens:

```
-rw-rw-r--  1 luke luke     12836 2011-11-01 11:30 mfc440cncupswrapper-1.0.1-1.i386.deb
-rw-rw-r--  1 luke luke   1087422 2011-11-01 11:17 mfc440cnlpr-1.0.1-1.i386.deb


luke@luke-desktop:~/Downloads$ sudo dpkg -l --force-all mfc440cnlpr-1.0.1-1.i386.deb
No packages found matching mfc440cnlpr-1.0.1-1.i386.deb.
luke@luke-desktop:~/Downloads$ 
```

When I try to install the .deb ... WTF?

---

### Post by Grimrian on 2011-11-13
I have the same problem with my wireless Brother DCP 585 CW. The driver etc. installed OK. I can print, but I keep having a message that the printer has no ink left and the printer properties shows that all color cartridges are empty while the printer itself and a Windows PC shows that all cartridges are OK.

---

### Post by FatFrog on 2011-12-16
I am also having the same issue. Has there been a resolution for this?

---

### Post by rcstook on 2012-01-25
I am also having this problem with the Brother MFC-495CW.
Though it prints just fine.
Every time I try to print, I get the message that all ink is empty.

I know this is not true.
Windows doesn't say this nor does the printer it self.

Any solution ideas?

---

### Post by muisudad on 2012-02-02
Add me to the list.  I have a brother MFC495cw.  It worked fine via wireless on 0910 ubuntu. When I installed it on 1110 it said it was out of ink but would print. Now I can't get it to print.  Help?:(

---

### Post by ubunkoop on 2012-04-15
same issue on Brother MFC-J410W ;(

being tax-time, anyone devise a work-around??? ~d

---

### Post by WinRiddance on 2012-04-18
Delete your printer and any previously downloaded files/instructions which used to work. Then go back to the Brother site and start from scratch. When I did that I noticed that driver files had changed in the past 4 - 6 months ... some of the instructions were slightly different too ... primarily because of the pre-checks that need to be done first. Also, there are "either or" lib files to be installed, but the lib file with ++ at the end showed me conflicts in the terminal for my MFC-J410W.

**I started completely from scratch** _after goofing around for the past 3 weeks_ trying to fix things. I must have installed the printer at least a dozen times. Going from scratch, slowly, methodically, did the trick for me right from the first try.

Gotta have LPR **and** CUPS drivers installed ... must install the LPR drivers first ... make sure required files are all there, such as ia32-libs and sane-utils via synaptic, and so on. Between recent (major) kernel 3.0 changes as well as driver updates and updated lib files, something appeared to have gone haywire with prior Brother printer installations that used to work ...
Good luck everyone! ;)

.

---

### Post by mörgæs on 2012-04-18
Moved to the hardware forum.

---

