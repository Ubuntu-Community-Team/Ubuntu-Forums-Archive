---
title: "HP Scanjet 5100C / ppscsi in Hardy"
date: 2008-05-04
forum: Hardware
---

### Post by haydnc on 2008-05-04
Once again I'm trying to get my scanner up and running in Hardy after upgrading.

Unfortunately the news isn't as good as it was with Feisty because my old instructions to get the ppscsi module compiled [(located here)]("http://ubuntuforums.org/showthread.php?t=441180") no longer work entirely.

The problem stems from an update to the way Ubuntu (actually I think it's the Kernel in general) handles what they call scatterlists in the 2.6.24 kernel. The reason for the change is a good one - it is apparently supposed to remove some of the speed bottlenecks that faster systems have encountered when using these scatterlists, sadly for me (and others like me wanting to get our old HP scanners up and running for whatever reason the ppscsi code is no longer maintained and hasn't been updated in upwards of 2 years.

Even sadder is that Hardy includes code and a kernel patch for ppscsi in its repos - but it doesn't work. This is a known bug [(see here)]("http://bugs.launchpad.net/ubuntu/+source/ppscsi/+bug/69023") but nothing is being done about it.

I'm hoping that some programming guru reads this, because I have to admit I'm not and trying to work out the fix just leaves me hopelessly confused. 

After following my earlier instructions I have isolated two snippets of code that need to be somehow updated to work with the new way scatterlists work, both in ppscsi.c (as downloaded from [penguin-breeder]("http://penguin-breeder.org/kernel/download/") and updated as per my earlier post (relating to feisty/gutsy).

```
static void ppsc_update_sg (PHA *pha)
{
	if ((!pha->cur_len) && pha->sg_count) {
		pha->sg_count--;
		pha->sg_list++;
		pha->cur_buf = page_address(pha->sg_list->page) + pha->sg_list->offset;
		pha->cur_len = pha->sg_list->length;
	}
}

```

and the line of code that references it - line 573 in the ppscsi.c file:

```
pha->cur_buf = page_address(pha->sg_list->page) + pha->sg_list->offset;

```

While I was flailing around trying to work out how to update the code I found [this page]("http://lwn.net/Articles/256368/") talking about what has been done to modify scatterlists that underlies the original code no longer working if thats any help.

Can anyone out there help?

I'll keep looking of course, but if someone can post the solution here that'd be awesome.

---

### Post by messelink on 2008-05-06
Struggling with exactly the same problem.

---

### Post by showgun22 on 2008-05-06
I guess I am even more newbie than you are since I am not even sure it is the same problem.
I have HP6100C connected to a PCI SCSI card Adaptec AHA2940U it was working fine if Feisty, Gutsy but since I have upgraded to Hardy the screen that use to come up at the beginning to load the SCSI does not.

When I type any of the following command line
lsscsi  lspci   lshw 
I can not see anything about the above Hardware It is like the scsi module does not exist?

If this is the same problem I sure hope some one is working on this since this is retrograding...

Or if some one knows how to fix this let me know

---

### Post by messelink on 2008-05-06
Nope, this thread is about running scsi over a parallel port with a module called ppscsi. Good luck with your problem, sorry I can't help you with it.

---

### Post by showgun22 on 2008-05-06
Got it I guess I will have to start my own thread...

---

### Post by Titik on 2008-05-11
Yes I have the same problem... If you find a solution (even if it's only a beginning) thank to post it!!! :KS

---

### Post by haydnc on 2008-05-15
Someone has posted a solution in a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/ppscsi/+bug/69023") which s/he claims will work on 8.04 (Hardy).

I'm planning to test it out tonight. I'll post whether it works and either instructions on how to do the changes or a copy of the changed files so that they can just be made and installed.

Keep watching this space.. or do it yourself if you get bored of waiting for me.  ;)

---

### Post by haydnc on 2008-05-15
I've done some initial testing and at least this version of the code compiles which is more than I can say for the last one I tested.

Unfortunately my scanner is at home so I can't test if this *really* works for a few hours. Follow the following instructions to get the ppscsi and epst modules to build and if anyone gets a chance to test this before I make it back with an update on whether it fixes the scanner please post here:

**Steps:**

Download the ppscsi-beta2-20060424 file from [penguin breeder]("http://penguin-breeder.org/kernel/download/").

Unpack the file - either using your preferred archive manager or the command line: 
```
tar zxvf ppscsi-beta2-20060424.tar.gz
```

*Open ppscsi.h and edit the following line:*

Line **16** - change from:
#include <linux/config.h>
to:
#include <linux/autoconf.h>

*Save and close ppscsi.h*

*Open ppscsi.c and edit the following lines:*

Line **486** - change from:
pha->cur_buf = page_address(pha->sg_list->page) + pha->sg_list->offset;
to:
pha->cur_buf = sg_virt(pha->sg_list); 

Line **573** - change from:
pha->cur_buf = page_address(pha->sg_list->page) + pha->sg_list->offset;
to:
pha->cur_buf = sg_virt(pha->sg_list);

Line **1148** - change from:
INIT_WORK(&pha->wq, ppsc_tq_int, pha);
to:
INIT_WORK(&pha->wq, ppsc_tq_int);

*Save and close ppscsi.c*

Type "make" at a command line and push enter to build the modules we need. Anyone who's never built anything before the word make should not have quote "" marks around it on the command line and I'm assuming that you've already installed the build-essential package and the kernel headers or you're not going to be able to do much more than edit some lines in the above files.

For the record - you can install both from the command line by typing the following and pressing enter:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Since the Makefile for ppscsi (still) has no instructions for installing these files we need to copy them to their new location manually:
```

sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
```

I've not tested the rest, but I'm fairly confident that the remaining steps are much the same as they were in my original instructions:

Next we need to tell the kernel that they exist:
```
sudo depmod
```

Lastly we need to load the modules:
```
sudo modprobe ppscsi
sudo modprobe epst

```

This will make the scanner useable until next time the computer is rebooted.

In order to make sure that the scanner is recognised from the moment you boot up it is necessary to edit /etc/modules and add the following two lines to the end of the file:
```
ppscsi
epst

```

I honestly have no clue if those last few steps are even needed in Hardy (Ubuntu 8.04). I'll hopefully get to test it tonight and post an update here. Also as I wrote earlier, I'll try to find a place to host and link the updated archive contaning the corrected ppscsi.h and ppscsi.c files.


Please note, I can't take any credit for working this all out. That was done by Jaska Kivelä and posted [here]("http://www.kivela.net/jaska/projects/ubuntu-ppscsi/"). I'm just putting it all together for those who search the Ubuntu forums first like I tend to.

As I said, if anyone makes it back with confirmation that this works before I do, please post here.

---

### Post by Kralnor on 2008-05-16
@haydnc

When I run 'make' I get the following error

```
make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Går til katalog '/usr/src/linux-headers-2.6.24-16-386'
  CC [M]  /home/kralnor/ppscsi-beta2/ppscsi.o
/home/kralnor/ppscsi-beta2/ppscsi.c: In function ‘ppsc_update_sg’:
/home/kralnor/ppscsi-beta2/ppscsi.c:486: fejl: ‘struct scatterlist’ has no member named ‘page’
/home/kralnor/ppscsi-beta2/ppscsi.c: In function ‘ppsc_engine’:
/home/kralnor/ppscsi-beta2/ppscsi.c:573: fejl: ‘struct scatterlist’ has no member named ‘page’
make[2]: *** [/home/kralnor/ppscsi-beta2/ppscsi.o] Fejl 1
make[1]: *** [_module_/home/kralnor/ppscsi-beta2] Fejl 2
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.24-16-386'
make: *** [all] Fejl 2
```

---

### Post by haydnc on 2008-05-16
Hi Kralnor,

It looks like you missed some steps. Those errors are generated by the ppscsi.c file on lines 486 and 573. Follow these instructions and it *will* build:

> Open ppscsi.c and edit the following lines:

**Line 486** - change from:
pha->cur_buf = page_address(pha->sg_list->page) + pha->sg_list->offset;
to:
pha->cur_buf = sg_virt(pha->sg_list);

**Line 573** - change from:
pha->cur_buf = page_address(pha->sg_list->page) + pha->sg_list->offset;
to:
pha->cur_buf = sg_virt(pha->sg_list);

**Line 1148** - change from:
INIT_WORK(&pha->wq, ppsc_tq_int, pha);
to:
INIT_WORK(&pha->wq, ppsc_tq_int);

Save and close ppscsi.c

~~~

For everyone else:

Unfortunately it still doesn't recognise my scanner even though all the instructions seem to work. I don't know if that's something strange in my setup, or a side effect of the lifeview tv tuner card in my machine.

If anyone has any further success please let me know.

---

### Post by Kralnor on 2008-05-16
It does *not* build for me even when I make the changes.

---

### Post by haydnc on 2008-05-17
@Kralnor

I'm not sure why it wouldn't compile for you - like I said, I didn't work this all out. I'm just following the steps as they were laid out by someone else and posting them here to try and help others.

I've put a copy of the modified files that do compile on my system [here]("http://haydnc.my-php.net/data/ppscsi.tar.gz").

My apologies if the link doesn't directly work - I've had some problems with that. If it doesn't try pasting the link directly into a fresh browser window - it should (hopefully) automatically download the file. (I do this by right clicking on the link, selecting copy link location, opening up a new browser window and pasting into the address bar. That works - where linking directly to the file *very* often does not. If people have ongoing trouble with this feel free to find another place for the file to be hosted and I'll update the link. Let me know.)

It definitely compiles on my Hardy with build-essential and headers installed as per my instructions on the previous page... but it also doesn't work with my scanner at present for reasons unknown.

Hopefully that file will just make it a little easier for someone else to test.

---

### Post by messelink on 2008-05-19
Thanks a lot the info Haydnc, works like a charm on my system. And many thanks to those that corrected the error, 

@Kralnor
I'm sure that you are trying to make the module without the edits that were posted before. Maybe your edits weren't written to the disk or they were saved in another file. Double check the file /home/kralnor/ppscsi-beta2/ppscsi.c especially the lines 486 and 573. There shouldn't be any reference in that line to "->page", because that is what broke the package in hardy.

On a side note, I think it's good practice to put source files for modules under /usr/src/modules.

---

### Post by Kralnor on 2008-05-19
Doh!

I was trying to run make in the wrong directory in the terminal. I had a copy of the module located in /home/kralnor/ppscsi-beta2 but the one I was actually editing was in /home/kralnor/Desktop/ppscsi-beta2

:oops:

Thanks for the instructions. My 5100C works fine once again.

---

### Post by haydnc on 2008-05-19
Now if I can just work out why it's working for everyone else but not me.

My system still picks up my LifeView TV card and ignores my scanner... before (with Gutsy) it detected both and gave me a choice of which one to use.

So confusing. <sigh>

---

### Post by Titik on 2008-05-19
Thanks for all... But for me it don't work for me too: I'm just following the steps and any error message.
But when I run xsane, my scanjet is not detected. So I try with gnomescan and I have this message

```

(flegita:7661): GnomeScan-DEBUG: gnomescan 0.4.1
(flegita:7661): GnomeScan-DEBUG: sane_init(0xbfacd7d8, NULL)
(flegita:7661): GnomeScan-DEBUG: SANE Version = 1.0.19
(flegita:7661): GnomeScan-DEBUG: sane_get_devices (0xbfacd7c8, FALSE)

```

I dont know if it's the same problem than haydnc...


PS Sorry for my english but I'm french so....

---

### Post by messelink on 2008-05-20
> **haydnc said:**
> 
My system still picks up my LifeView TV card and ignores my scanner... before (with Gutsy) it detected both and gave me a choice of which one to use.
Did you try disconnecting the TV card and see if the system detects the scanner than? Then you know if it's really the two cards interfering or if this build of the module just doesn't like your scanner...

What version of the module did you use before in Gutsy? Because I have always build and used the ppsci-beta2 module (with some edits) in Gutsy as well.

@Titik
Sorry, I have no idea what the problem could be.

---

### Post by Titik on 2008-05-20
So maybe I found a beginning of solution:
when I'm runing
```
 sane-find-scanner
```
I have
```
found SCSI processor "HP C5190A 3740" at /dev/sg4
```
SO it's detected !!!

Sombody can show what he get  with "sane-find-scanner" and  publish his
 /etc/sane.d/hp.conf ??

---

### Post by messelink on 2008-05-23
```
pim@rollercoaster:~$ cat /etc/sane.d/hp.conf 
scsi HP
# Uncomment the following if you have "Error during device I/O" on SCSI
#   option dumb-read
#
# The usual place for a SCSI-scanner on Linux
/dev/scanner
#
# USB-scanners supported by the hp-backend
# HP ScanJet 4100C
usb 0x03f0 0x0101
# HP ScanJet 5200C
usb 0x03f0 0x0401
# HP ScanJet 62X0C
usb 0x03f0 0x0201
# HP ScanJet 63X0C
usb 0x03f0 0x0601
#
# Uncomment the following if your scanner is connected by USB,
# but you are not using libusb
# /dev/usb/scanner0
#   option connect-device

```

I don't have sane-utils installed, so I can't check your other question. Hope this helps.

You might consider creating your own thread for your problem, so the right people will read it and might help you.

---

### Post by haydnc on 2008-05-27
Interestingly enough since I'm experiencing the same issue as Titik following the compile and install of ppscsi this might be the best place for the discussion to continue.

Since this is the first time I've run into any issues with ppscsi it's conceivable that someone else following this thread will run into the same thing eventually.

@messelink
No, I have not disconnected the troublesome TV card, mostly because I need a solution that doesn't involve me not being able to use some of my hardware. Given enough time and the failure of all other options I will pull it out for testing purposes, but I'd really rather not have to.

I've also not had a chance yet to compare the differences if any between the posted hp.conf file and my own, hopefully there will be some answers in there.

Do you happen to know if your scanner is actually located at /dev/scanner, or indeed if that node even exists in your /dev list? I don't believe it exists for me which might also be a part of the problem. (Must remember to check up on that tonight.)

---

### Post by haydnc on 2008-05-28
Sadly my hp.conf file is exactly the same as the one posted here, but I definitely don't have the /dev/scanner node that it refers to.

Does anyone (that this works for) have any idea how their scanner is identified by their system?

(Still have not got time to haul the tv card out of my machine - that'll come later.)

---

### Post by messelink on 2008-05-29
Sorry, I'm running a different kernel at the moment to see if I can solve the problem of the computer freezing up when using bit torrent since the upgrade to Hardy and I have not yet build the modules.

---

### Post by Titik on 2008-06-03
@haydnc

I don't have a solution but try to:
1 install the package sane-utils
2 check result when you 're doing
```
sudo sane-find-scanner
```

For me, I think that your /dev/scanner doesn't refer to your scanner and we have the same problem.
I tried (for me,  "HP C5190A 3740" at /dev/sg4)
1  sudo chmod 777 /dev/sg4
2  sudo ln -s /dev/sg4 /dev/scanner
3  sudo chmod 777 /dev/scanner
But when I'm restarting my system, /dev/scanner disappear..
I have not enough time to resolve this problem, but maybe it can help you...

---

### Post by Bablefish on 2008-06-03
Call this just an observation, but after reading many of your post. I have a question for you, did you go to hp.com and download the linux drivers? I did and haven't had a single problem since.

---

### Post by haydnc on 2008-06-05
@Bablefish

Where did you find those drivers? When I go to the HP website and search for drivers for the Scanjet 5100C all it comes up with are Windows drivers.

---

### Post by blackdalek on 2008-06-06
> **haydnc said:**
> 
**Steps:**

Download the ppscsi-beta2-20060424 file from [penguin breeder]("http://penguin-breeder.org/kernel/download/").

Unpack the file - either using your preferred archive manager or the command line: 
```
tar zxvf ppscsi-beta2-20060424.tar.gz
```

*Open ppscsi.h and edit the following line:*

Line **16** - change from:
#include <linux/config.h>
to:
#include <linux/autoconf.h>

*Save and close ppscsi.h*

*Open ppscsi.c and edit the following lines:*

Line **486** - change from:
pha->cur_buf = page_address(pha->sg_list->page) + pha->sg_list->offset;
to:
pha->cur_buf = sg_virt(pha->sg_list); 

Line **573** - change from:
pha->cur_buf = page_address(pha->sg_list->page) + pha->sg_list->offset;
to:
pha->cur_buf = sg_virt(pha->sg_list);

Line **1148** - change from:
INIT_WORK(&pha->wq, ppsc_tq_int, pha);
to:
INIT_WORK(&pha->wq, ppsc_tq_int);

*Save and close ppscsi.c*

Type "make" at a command line and push enter to build the modules we need. Anyone who's never built anything before the word make should not have quote "" marks around it on the command line and I'm assuming that you've already installed the build-essential package and the kernel headers or you're not going to be able to do much more than edit some lines in the above files.

For the record - you can install both from the command line by typing the following and pressing enter:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Since the Makefile for ppscsi (still) has no instructions for installing these files we need to copy them to their new location manually:
```

sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
```

I've not tested the rest, but I'm fairly confident that the remaining steps are much the same as they were in my original instructions:

Next we need to tell the kernel that they exist:
```
sudo depmod
```

Lastly we need to load the modules:
```
sudo modprobe ppscsi
sudo modprobe epst

```

This will make the scanner useable until next time the computer is rebooted.

In order to make sure that the scanner is recognised from the moment you boot up it is necessary to edit /etc/modules and add the following two lines to the end of the file:
```
ppscsi
epst

```


I followed all these instructions and didn't get any errors at any stage.
Xsane still can't detect my scanner.
Any idea why?
Using hardy 8.04 and a HP Scanjet 5100c (para port)

sudo sane-find-scanner outputs...

found SCSI processor "HP C5190A 3740" at /dev/sg3

sudo scanimage -L outputs....

device `hp:/dev/sg3' is a Hewlett-Packard C5190A flatbed scanner

Yet XSane still can't find the scanner.


EDIT: I did a chmod 777 /dev/sg3 and then Xsane found the scanner. It seem to work now.

---

### Post by haydnc on 2008-06-09
@blackdalek

> EDIT: I did a chmod 777 /dev/sg3 and then Xsane found the scanner. It seem to work now.

Thanks blackdalek, I actually hadn't considered that as a possible solution.
I've not had a chance to try it yet but if it works it could resolve the one outstanding issue that I've been having getting this to work on my own machine.

I'll post here once I've tested it.
:)

---

### Post by haydnc on 2008-06-10
That did the trick!

So the final step in these instructions is:

If your HP ScanJet 5100C still doesn't work after you follow the other instructions and install ppscsi do the following:

```
sudo sane-find-scanner
```

If sane-find-scanner isn't working you probably need to install sane-utils by typing:

```
sudo apt-get install sane-utils
```

Then try the sudo sane-find-scanner command above.

Somewhere in the output from sane-find-scanner will be a line that resembles:

> found SCSI processor "HP C5190A 3740" at /dev/sg4

Take note of what it says after /dev at the end of the line then type:

```
sudo chmod 777 /dev/sg4 (or whatever matches the above line)
```

Your scanner should then work.

I do notice that someone else said they tried that coupled with creating the node /dev/scanner but it didn't stay active past a reboot. I suspect that just changing the mode on the /dev/<whatever> should fix the problem but if it doesn't continue working for me after my next reboot I'll post something here.

Edit: I have discovered that changing the mode of /dev/sg4 is a temporary fix after all, however adding myself to the scanner user group (or giving myself permission to use scanners) is a permanent fix. Sorry, I don't have the code to do this from the command line to hand - I just did it under System - Administration - Users and Groups menu and checked the Use scanners User Privilege.

---

### Post by bwallum on 2008-06-14
> **showgun22 said:**
> I guess I am even more newbie than you are since I am not even sure it is the same problem.
I have HP6100C connected to a PCI SCSI card Adaptec AHA2940U it was working fine if Feisty, Gutsy but since I have upgraded to Hardy the screen that use to come up at the beginning to load the SCSI does not.

When I type any of the following command line
lsscsi  lspci   lshw 
I can not see anything about the above Hardware It is like the scsi module does not exist?

If this is the same problem I sure hope some one is working on this since this is retrograding...

Or if some one knows how to fix this let me know

Hi, I'm having a similar problem getting a scsi scanner to work on 8.04.

For some reason the usb devices I have (web cam and memorycard/usb hub) are called scsi devices. You may therefore need to set your scsi scanner to a new number. You can access the scsi card setup at POST by typing in <ctrl>A as the POST reports the card. If POST does not report the card then check your BIOS setup to make sure your pci slots are enabled.

I need to make a few experiments now but have posted this to start the dialogue.

---

### Post by haydnc on 2008-06-14
@bwallum

It might be worth starting a new thread relating to the scanner you've got if the instruction for the HP ScanJet 5100C don't work for you. It certainly will increase the chances of it being found by the right people.


~~~

For everyone else, one thing it might pay to remember with these instructions:

Every time a new kernel update comes out you'll have to do this again.

I've no idea if ppscsi compiled under an earlier 2.6.24 kernel will work if you copy them across, they might. I've just found it's easy to re-run the make and copy the new files back to the parport directory.

---

### Post by alaswat on 2008-09-20
Does anybody know why it happens to me this:
when I do make it compiles but throws this warning, which means that i won't be able to load the module, as there is an undefined symbol, 
WARNING: "sg_virt" [/usr/src/ppscsi-beta2/ppscsi.ko] undefined!

I found sg_virt is declared on
include/linux/scatterlist.h

Currently usin Gutsy with 2.6.22-15-generic
Thanks

---

### Post by haydnc on 2008-10-02
I haven't updated this recently myself because I've not needed to use my scanner, but I'd guess from the error that either you skipped the following section entirely, or they've changed something else meaning my instructions don't work any more and wont until someone figures out the next work around...


These lines from the instructions are the only ones that reference sg_virt so that'd be the first place I'd look to try and solve your error. I'll give it another go tonight and see if I can still get it working for me and I'll post here to let everyone know.

```
Open ppscsi.c and edit the following lines:

Line 486 - change from:
pha->cur_buf = page_address(pha->sg_list->page) + pha->sg_list->offset;
to:
pha->cur_buf = sg_virt(pha->sg_list);

Line 573 - change from:
pha->cur_buf = page_address(pha->sg_list->page) + pha->sg_list->offset;
to:
pha->cur_buf = sg_virt(pha->sg_list);

Line 1148 - change from:
INIT_WORK(&pha->wq, ppsc_tq_int, pha);
to:
INIT_WORK(&pha->wq, ppsc_tq_int);

Save and close ppscsi.c
```


~~~

I've just redone this on my machine - Ubuntu Hardy fully updated to 8.04.1 following my instructions and it definitely still works. If things are not going right for you I can only suggest you double check your editing of the lines in the ppscsi.c and ppscsi.h (I think) files.

---

### Post by Skippy_X on 2008-12-31
Hullo!

I thought I'd better say **THANK YOU**!!!!!! for this thread.

I have a Win Vista laptop and a Lexmark X8350 all-in-one printer that was driving me batty. Sometimes it would scan, sometimes not. It seemed to do what it wanted to do (or not) when it wanted to (or not) - and I couldn't find a fix for it online.

That being the case, I thought I'd find a Linux compatible scanner and just do my work scanning on my Linux box.

I found a ScanJet 5100C at a thrift shop/second hand store for $7 (US). 

These instructions worked beautifully and I'm now in the midst of scanning customer service forms for my boss - who was getting a bit impatient @ the delays.

The Ubuntu Forums are fantastic!

Oh - and the Lexmark is going to my g/f's daughter. She's got a Win XP box on which the drivers and applications should likely work.

---

### Post by Kralnor on 2009-01-31
Seems like the driver has broken yet again with the latest version of Ubuntu.

I am running 8.10 Intrepid Ibex and I get the following output when I run make

```

kralnor@kralnor-desktop:~/Desktop/ppscsi-beta2$ make
make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Går til katalog '/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/kralnor/Desktop/ppscsi-beta2/ppscsi.o
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c: In function ‘ppsc_start’:
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:425: fejl: ‘struct scsi_cmnd’ has no member named ‘use_sg’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:428: fejl: ‘struct scsi_cmnd’ has no member named ‘request_buffer’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:434: fejl: ‘struct scsi_cmnd’ has no member named ‘request_bufflen’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c: In function ‘ppsc_engine’:
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:568: fejl: ‘struct scsi_cmnd’ has no member named ‘use_sg’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:572: fejl: ‘struct scsi_cmnd’ has no member named ‘request_buffer’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:576: fejl: ‘struct scsi_cmnd’ has no member named ‘request_buffer’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:577: fejl: ‘struct scsi_cmnd’ has no member named ‘request_bufflen’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:623: fejl: ‘struct scsi_cmnd’ has no member named ‘request_buffer’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c: In function ‘ppsc_cleanup’:
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:818: fejl: ‘struct scsi_cmnd’ has no member named ‘use_sg’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:819: fejl: ‘struct scsi_cmnd’ has no member named ‘request_buffer’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:820: fejl: ‘struct scsi_cmnd’ has no member named ‘request_bufflen’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c: In function ‘ppsc_inquire’:
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:1017: fejl: ‘struct scsi_cmnd’ has no member named ‘use_sg’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:1018: fejl: ‘struct scsi_cmnd’ has no member named ‘request_buffer’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:1019: fejl: ‘struct scsi_cmnd’ has no member named ‘request_bufflen’
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c: In function ‘ppsc_detect’:
/home/kralnor/Desktop/ppscsi-beta2/ppscsi.c:1148: advarsel: assignment from incompatible pointer type
make[2]: *** [/home/kralnor/Desktop/ppscsi-beta2/ppscsi.o] Fejl 1
make[1]: *** [_module_/home/kralnor/Desktop/ppscsi-beta2] Fejl 2
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Fejl 2

```

---

### Post by koronet on 2009-02-18
> **Kralnor said:**
> Seems like the driver has broken yet again with the latest version of Ubuntu.

I am running 8.10 Intrepid Ibex and I get the following output when I run make



I have the same problem. If anybody find a solution please post it!! Thanks.

---

### Post by haydnc on 2009-02-20
Sadly it doesn't look like there is a fix out there for this yet but I'll keep looking. Its the first time I've been glad that I've not yet upgraded my main PC's OS from 8.04.x

If there are any programmers out there who know what modifications need to be made to the ppscsi.h file to make this work this time, please feel free to post it here.
:)

---

### Post by iadegesso on 2009-06-14
I've found a solution.

It is online on my website at [http://www.iadegesso.netsons.org/ppscsi0_92patch2_6_27up.html#ppscsisoluzione](http://www.iadegesso.netsons.org/ppscsi0_92patch2_6_27up.html#ppscsisoluzione) (in italian)

Sorry for my bad english

>>> NEW <<<
I've posted a bad path version on my website. Now, correct version was uploaded. Sorry for this stupid error.

---

### Post by walterp98@gmail.com on 2009-06-19
This is slightly OT, but I'm running Jaunty 9.04 ...

Has anyone used these instructions to get a Scanjet 5100c to work under this version?

Thanks in advance.

WP

>>>> EDIT >>>>>
I let google translate the page above and I have success using my scanner now (though I had to chmod 777 /dev/sg4 (my scanner for xsane to see it).

Thanks for the help!

>>>> EDIT >>>>
I used
```
sudo addgroup scanner
sudo adduser myUser scanner

```
to get around the chmod issue ... good luck to all.

---

### Post by BCPlanner on 2009-08-11
> **Bablefish said:**
> Call this just an observation, but after reading many of your post. I have a question for you, did you go to hp.com and download the linux drivers? I did and haven't had a single problem since.
 
The SANE PROJECT URL for HP scanners is 
[http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)
 
(http:// [www.sane-project.org/sane-mfgs.html]("http://www.sane-project.org/sane-mfgs.html") #Z-HEWLETT-PACKARD) [delete spaces]
 
The SANE base URL is [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)
 
and includes scanners, still, & video cameras
 
Worth a bookmark.
 
(Does it work? Waiting for 9.04 to see.)

---

### Post by haydnc on 2009-08-12
Back again with the latest update... 

Regarding the post from BCPlanner - those links basically tell us all what we know already. That our scanner will work just fine, as long as you've installed ppscis and epst, which is what this thread is really all about.

I'd also like to thank iadegesso for putting together the latest fix for those of us still struggling to use our old HP 5100C scanners.

It appears that he is the programmer that we were looking for who a few posts back I asked to look into a solution for us!

I'm just keeping a copy of the instructions here for those who don't want to wade through translating his page from Italian or who need some step-by-step instructions.

No instructions will be provided for those not wanting to use the terminal. If you want that old scanner to run, you're going to type some stuff in the terminal - get used to it. :)

As always you first need to have installed everything you need to successfully build packages in Ubuntu. Open a terminal and type:
```
sudo apt-get install build-essential patch linux-headers-`uname - r`
```

Download ppscsi-beta2-20060424.tar.gz from [http://penguin-breeder.org/kernel/download/ppscsi-beta2-20060424.tar.gz](http://penguin-breeder.org/kernel/download/ppscsi-beta2-20060424.tar.gz) 

Download the updated patch file that iadegesso has put together. It is called ppscsi-patch-2_6_27up.tar.gz and can be found on iadegesso's webpage (follow the link he has kindly provided and download the patch file you see listed under the text "Allegati"). He has also kindly provided a copy of the original file.

   
Change directory in the terminal to where ever you downloaded the files above. Enter each of the following lines into your terminal window:

```
tar zxvf ppscsi-beta2-20060424.tar.gz
```
```
tar zxvf ppscsi-patch-2_6_27up.tar.gz
```
```
mv ppscsi.*.patch ppscsi-beta2
```
```
cd ppscsi-beta2
```

After each of the following lines you should see confirmation that a patch has been applied to the original file...

```
patch -Np1 -i ppscsi.c.patch
```
```
patch -Np0 -i ppscsi.h.patch
```

```
make
```

At this point if you've done everything right you should see the wonders of c code compiling producing the files we need. I got a couple of messages about "assignment from incompatible pointer type" but they were not enough to stop the code from compiling. 

The end result is a whole bunch of new files in the directory you're in. The important ones are ppscsi.ko and epst.ko

We need to copy them to a location where they'll be of some use to us:

```
sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
```

Then tell our system to detect and enable them:

```
sudo depmod
```
```
sudo modprobe ppscsi
```
```
sudo modprobe epst
```

We also need to set things up so that these load automatically when we restart. Use your favourite editor to edit /etc/modules and add the following lines at the bottom of the file:
      ppscsi
      epst
e.g.
```
gksudo gedit /etc/modules
``` 
Add ppscsi and epst each on its own line then save and exit the file.

Lastly follow the instructions added by walterp so that you don't have to mess around with changing permissions each time you want to use your scanner:
```
sudo addgroup scanner
sudo adduser <your username here> scanner
```

Obviously put your login/user name in where appropriate.

One of these days I might try to find a more permanent host for this kind of thing which can be linked to in this tread, but to be honest I keep hoping they'll fix the source packages in Ubuntu so that none of it is necessary.

Also as usual I'm not at home at the moment so I can't test this with my scanner. I'll try to test it tonight and post confirmation that it all works.

~~~

Thanks to all those who have helped keep our old parallel port ScanJet 5100C flatbed scanners alive!
Edit: I've just realised that we really need a forum mod to change the name of the thread so that it's not Hardy-Heron only. If any read this could the name perhaps be changed to HP Scanjet 5100C / ppscsi in Ubuntu?

---

### Post by messelink on 2009-08-28
Thanks a lot all for the good work!

Some small typos:
> **haydnc said:**
> 
Download the updated patch file that iadegesso has put together. It is called ppscsi-pat**c**h-2_6_27up.tar.gz and can be found on iadegesso's webpage
[..]
tar zxvf ppscsi-pat**c**h-2_6_27up.tar.gz
[..]
sudo cp ppscsi.ko epst.ko /lib/modules/`uname **-r**`/kernel/drivers/parport

And you might need to change the group of the node in /dev to scanner. After you load the epst.ko you should do a "dmesg" to see to what node it is bound to. You should see something like [579138.038126] scsi 6:0:0:0: Attached scsi generic sg2 type 3, which means your scanner is at /dev/sg2. Then you do a sudo chown :scanner /dev/sg2 . I don't know if this is persistent after a reboot though...

---

### Post by haydnc on 2009-08-28
Thanks messelink. I was obviously having a worse typing day than I thought. I've edited my post (again) to fix the remaining errors.

I've not had a chance to try this out yet - my scanner is not set up at the moment. Has anyone actually given it a go with the updated instructions who can confirm that it works?

---

### Post by iadegesso on 2009-09-02
hi there, I've found a solution for scanner ownership.
> **messelink said:**
> sudo chown :scanner /dev/sg2 is not a permanent solution because it is lost on reboot. Also, while rebooting, the device name may change, so this scripting command is unhelpful. 

You must write an appropriate udev rule in the file /etc/udev/rules.d/45-libsane.rules:

SUBSYSTEM=="scsi_generic",ATTRS{type}=="3", NAME="%k", SYMLINK="scanner%n", MODE="0777", GROUP="scanner"

A more detailed description can be found on my website at [http://www.iadegesso.netsons.org/ppscsi0_92patch2_6_27up.html#ppscsisoluzione](http://www.iadegesso.netsons.org/ppscsi0_92patch2_6_27up.html#ppscsisoluzione) in note 2.

First of all, however, do not forget to execute commands
> **haydnc said:**
> 
```
sudo addgroup scanner
sudo adduser <your username here> scanner
```

---

### Post by haydnc on 2009-09-29
For what it is worth I've verified that everything up to this point works in 9.04 except the last step provided by iadegesso, and that is only because I've not had to reboot my machine yet.

For those who love the step by step instructions or who have problems with anything so far let us know.. I'll keep on trying to help as long as I still have my scanner.
:)

---

### Post by Corsu on 2009-09-30
Hi guys, 

I'm running ubuntu 9.04 and the instructions from haydnc worked well.
But for sane to find & detect my Scanjet 5100c I had to do a chmod 777 /dev/sg4.
Did someone tried the udev rule method with success with jaunty ? 

And finally Great thanks to all the contributors of this post !

---

### Post by haydnc on 2009-09-30
I tested the solution provided by iadegesso successfully last night.

For those wanting the step by step:
```

gksudo gedit /etc/udev/rules.d/45-libsane.rules

```

Paste in the following:
```

SUBSYSTEM=="scsi_generic",ATTRS{type}=="3",NAME="%k",SYMLINK="scanner%n",MODE="0777",GROUP="scanner"

```

Save and exit the file.

Please note, as stated by iadegesso below this will only work if you've already followed the earlier instructions for adding a group called scanner then adding yourself to that group. There are instructions for doing this about 3 posts up.

The really interesting thing is that this could all change in a month when Karmic Koala is released. We know it works for Jaunty - if anyone is brave enough to install the beta when it lands later today and see if this still works we'd love to hear about it.

Otherwise things'll probably go back on hold until I've gotten 9.10 installed on my machine again.
:)

---

### Post by messelink on 2009-10-26
If you are getting an error saying device not found when doing modprobe epst, before you try anythig else, make sure your scanner is plugged in...

Ahem... =P

Thanks for the good work guys, keep it up!

(No, I haven't tried Karmic yet but I'd love to hear if someone has)

---

### Post by haydnc on 2009-10-26
Depending on how organised I am I might be able to provide an answer to how well this works under Karmic next week (after the official release). Can't promise anything though as I'm rarely in a hugh rush to go through the upgrade process. :)

---

### Post by Younio on 2009-11-06
^^^

  Hello everyone,
Thanks to this forum I have successfully got working my printer under Jounty, but there is a problem with Karmic release. 
I haven't got time to wait for haydnc, so I tried it myself in Karmic. 
Everything went well like in Jaunty, except this command:
> **haydnc said:**
> 
```
sudo modprobe epst
```
When I type the command, it gets me empty line, like its processing something. When I try to close the terminal it says that there is a process running. Then after about 2 hours i get this message: ```
FATAL: Error inserting epst (/lib/modules/2.6.31-14-generic/kernel/drivers/parport/epst.ko): No such device 
``` 
Any ideas what could be causing this?

Any help would be appreciated. : 7

---

### Post by haydnc on 2009-11-08
Well I can confirm that as Younio has said there is **something** not right with epst in karmic.

I've not been patient enough to leave the modprobe running so I don't know if I'm going to get the same error he has reported but I can confirm that I get the same blank line when running modprobe epst.

Running make definitely generates all the files that it should. 

There is an 'error' during the build process (see code below) however once more I'm not enough of a programmer to work out if it's the cause of epst no longer working as it should.

```

make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.o
/home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.c: In function &#8216;ppsc_cleanup&#8217;:
/home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.c:849: warning: assignment from incompatible pointer type
/home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.c: In function &#8216;ppsc_detect&#8217;:
/home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.c:1192: warning: assignment from incompatible pointer type
  CC [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/t348.o
  CC [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/t358.o
  CC [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/onscsi.o
  CC [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/epsa2.o
  CC [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/epst.o
  CC [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/vpi0.o
  CC [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/sparcsi.o
  Building modules, stage 2.
  MODPOST 8 modules
  CC      /home/haydnc/build/ppscsi/ppscsi-beta2/epsa2.mod.o
  LD [M]  /home/haydnc/builde/ppscsi/ppscsi-beta2/epsa2.ko
  CC      /home/haydnc/build/ppscsi/ppscsi-beta2/epst.mod.o
  LD [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/epst.ko
  CC      /home/haydnc/build/ppscsi/ppscsi-beta2/onscsi.mod.o
  LD [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/onscsi.ko
  CC      /home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.mod.o
  LD [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.ko
  CC      /home/haydnc/build/ppscsi/ppscsi-beta2/sparcsi.mod.o
  LD [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/sparcsi.ko
  CC      /home/haydnc/build/ppscsi/ppscsi-beta2/t348.mod.o
  LD [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/t348.ko
  CC      /home/haydnc/build/ppscsi/ppscsi-beta2/t358.mod.o
  LD [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/t358.ko
  CC      /home/haydnc/build/ppscsi/ppscsi-beta2/vpi0.mod.o
  LD [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/vpi0.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic
```

For those programmers out there, who've been keen/brave enough to upgrade to karmic, the two errors above are lines 849 of ppscsi.c (the line in red):
```
#if LINUX_VERSION_CODE > KERNEL_VERSION(2,6,24)
cmd->sdb.table.nents = 0;
[COLOR="Red"]cmd->sdb.table.sgl = (char *) cmd->sense_buffer;[/COLOR]
cmd->sdb.length = sizeof(cmd->sense_buffer);
```
and line 1192:
```
INIT_WORK(&pha->wq, ppsc_tq_int);
```

If anyone has any ideas on how to get this working again, please speak up.
:)

Edit: Confirmed I get that same error message:
```
FATAL: Error inserting epst (/lib/modules/2.6.31-14-generic/kernel/drivers/parport/epst.ko): No such device
```
Anyone know why? Or anyone out there who found a work around?.

---

### Post by haydnc on 2009-12-14
I have not finished searching everywhere yet, but it's beginning to look a lot like they've dropped ppscsi support entirely in 9.10.

For now I'd suggest that everyone who wants to keep using the HP5100C scanner (parallel port) stick with 9.04.

If anyone has found a way to get the scanner working under 9.10 please let us know - it appears that the problem at this point is actually with the epst module rather than the ppscsi module if that is any help at all. Possibly its a place to start looking.

---

### Post by tcsoft on 2009-12-18
hi!

i've compiled the modules according to these instructions found [here]("http://www.iadegesso.netsons.org/ppscsi0_92patch2_6_27up.html")
modprobe ppscsi works fine. but when inserting epst i get the output on the console: "Segmentation fault" and the following dmesg-output:

```

[  135.047811] ppSCSI 0.92 (0.92) installed
[  150.769679] BUG: unable to handle kernel paging request at 9c9ae586
[  150.769817] IP: [<f8f6c722>] :ppscsi:ppsc_inquire+0x62/0xa0
[  150.769909] *pdpt = 000000003619d001 *pde = 0000000000000000
[  150.769918] Oops: 0002 [#1] SMP
[  150.770007] Modules linked in: epst(+) ppscsi ppdev wmi video output sbs sbshc pci_slot container battery ac ipv6 af_packet iptable_filter ip_tables x_tables coretemp w83627ehf hwmon_vid lp loop evdev parport_pc parport psmouse serio_raw button pcspkr sis_agp agpgart shpchp pci_hotplug jfs sd_mod crc_t10dif sg usb_storage libusual sata_sis pata_sis pata_acpi ata_generic libata scsi_mod sis900 mii ehci_hcd dock ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  150.770007]
[  150.770007] Pid: 5906, comm: modprobe Not tainted (2.6.27-16-server #1)
[  150.770007] EIP: 0060:[<f8f6c722>] EFLAGS: 00010246 CPU: 0
[  150.770007] EIP is at ppsc_inquire+0x62/0xa0 [ppscsi]
[  150.770007] EAX: 9c9ae586 EBX: f2dc7e0e ECX: 00000000 EDX: 00000012
[  150.770007] ESI: f2dc7e5a EDI: 00000000 EBP: f2dc7e1c ESP: f2dc7a10
[  150.770007]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[  150.770007] Process modprobe (pid: 5906, ti=f2dc6000 task=f2cb25b0 task.ti=f2dc6000)
[  150.770007] Stack: f41d7800 000000d0 00000000 00000001 00881ba0 f2cfae00 c209e150 00000000
[  150.770007]        f2cb25dc 00003a5d f2cb25dc f2dc7a64 c0127cc9 007eb1ac 00000023 17065ef2
[  150.770007]        00000000 00000000 f2cb25dc c21cadbc c21cad80 f2dc7a80 c012a995 c0531d80
[  150.770007] Call Trace:
[  150.770007]  [<c0127cc9>] ? update_curr+0x89/0x110
[  150.770007]  [<c012a995>] ? dequeue_entity+0x15/0x180
[  150.770007]  [<c0131e49>] ? dequeue_task_fair+0x49/0x50
[  150.770007]  [<c01287ef>] ? dequeue_task+0xcf/0x130
[  150.770007]  [<c0108dc6>] ? __switch_to+0xa6/0x160
[  150.770007]  [<c012fc4b>] ? finish_task_switch+0x2b/0xe0
[  150.770007]  [<c038c789>] ? schedule+0x429/0x790
[  150.770007]  [<c01958f9>] ? lru_cache_add+0x9/0x60
[  150.770007]  [<c01e8ad0>] ? mpage_end_io_read+0x0/0x70
[  150.770007]  [<c01e89e1>] ? mpage_bio_submit+0x21/0x30
[  150.770007]  [<c038cb1c>] ? io_schedule+0x2c/0x40
[  150.770007]  [<c014f306>] ? finish_wait+0x16/0x70
[  150.770007]  [<c038cfc4>] ? __wait_on_bit_lock+0x64/0x90
[  150.770007]  [<c0194bf7>] ? __do_page_cache_readahead+0x137/0x1e0
[  150.770007]  [<c018c930>] ? sync_page+0x0/0x60
[  150.770007]  [<c018c3f2>] ? __lock_page+0x82/0x90
[  150.770007]  [<c014f200>] ? wake_bit_function+0x0/0x60
[  150.770007]  [<c0158252>] ? clocksource_get_next+0x42/0x50
[  150.770007]  [<c0156eea>] ? update_wall_time+0x47a/0x7f0
[  150.770007]  [<c015696b>] ? getnstimeofday+0x5b/0x120
[  150.770007]  [<c0158252>] ? clocksource_get_next+0x42/0x50
[  150.770007]  [<c0156eea>] ? update_wall_time+0x47a/0x7f0
[  150.770007]  [<c015696b>] ? getnstimeofday+0x5b/0x120
[  150.770007]  [<c013e1b6>] ? set_normalized_timespec+0x16/0x90
[  150.770007]  [<c015c0c7>] ? timer_stats_update_stats+0x17/0x250
[  150.770007]  [<c0127cc9>] ? update_curr+0x89/0x110
[  150.770007]  [<c038e2d1>] ? _spin_lock_irqsave+0x31/0x40
[  150.770007]  [<c01445fc>] ? __mod_timer+0xac/0xf0
[  150.770007]  [<f888923b>] ? scan_async+0x17b/0x1b0 [ehci_hcd]
[  150.770007]  [<f888a650>] ? ehci_watchdog+0x0/0x60 [ehci_hcd]
[  150.770007]  [<c01446ff>] ? mod_timer+0x3f/0x80
[  150.770007]  [<f888a697>] ? ehci_watchdog+0x47/0x60 [ehci_hcd]
[  150.770007]  [<c038e2fb>] ? _spin_lock_irq+0x1b/0x20
[  150.770007]  [<c0143cae>] ? run_timer_softirq+0x17e/0x210
[  150.770007]  [<f888a650>] ? ehci_watchdog+0x0/0x60 [ehci_hcd]
[  150.770007]  [<f888a650>] ? ehci_watchdog+0x0/0x60 [ehci_hcd]
[  150.770007]  [<c0181ace>] ? __rcu_process_callbacks+0xe/0x200
[  150.770007]  [<c013ee46>] ? __do_softirq+0xf6/0x120
[  150.770007]  [<c013f034>] ? irq_exit+0x44/0x90
[  150.770007]  [<c0119b4d>] ? smp_apic_timer_interrupt+0x5d/0x90
[  150.770007]  [<c025db4e>] ? delay_tsc+0xe/0x70
[  150.770007]  [<c025dc99>] ? __udelay+0x39/0x3c
[  150.770007]  [<c025db4e>] ? delay_tsc+0xe/0x70
[  150.770007]  [<c025dc99>] ? __udelay+0x39/0x3c
[  150.770007]  [<f8f759b5>] ? epst_disconnect+0x1b5/0x400 [epst]
[  150.770007]  [<f8f7636a>] ? epst_test_proto+0x10a/0x170 [epst]
[  150.770007]  [<f8ec11a9>] ? parport_pc_save_state+0x9/0x40 [parport_pc]
[  150.770007]  [<f8eb5384>] ? parport_release+0x74/0x170 [parport]
[  150.770007]  [<f8f6c81c>] ? ppsc_test_mode+0xbc/0x190 [ppscsi]
[  150.770007]  [<c01fd7d8>] ? proc_mkdir_mode+0x38/0x50
[  150.770007]  [<c038d208>] ? mutex_unlock+0x8/0x20
[  150.770007]  [<f890e2c7>] ? scsi_proc_hostdir_add+0x37/0xe0 [scsi_mod]
[  150.770007]  [<f8902dc0>] ? scsi_host_alloc+0x2a0/0x2b0 [scsi_mod]
[  150.770007]  [<f8906820>] ? scsi_error_handler+0x0/0x130 [scsi_mod]
[  150.770007]  [<f8902de8>] ? scsi_register+0x18/0x80 [scsi_mod]
[  150.770007]  [<f8f6d39d>] ? ppsc_detect+0x40d/0x560 [ppscsi]
[  150.770007]  [<f8f6c3a0>] ? ppsc_wake_up+0x0/0xd0 [ppscsi]
[  150.770007]  [<f8856000>] ? init_this_scsi_driver+0x0/0xec [epst]
[  150.770007]  [<f8f7401a>] ? epst_detect+0x1a/0x20 [epst]
[  150.770007]  [<f8856049>] ? init_this_scsi_driver+0x49/0xec [epst]
[  150.770007]  [<f8856000>] ? init_this_scsi_driver+0x0/0xec [epst]
[  150.770007]  [<c010302f>] ? do_one_initcall+0x2f/0x160
[  150.770007]  [<c0154384>] ? __blocking_notifier_call_chain+0x14/0x70
[  150.770007]  [<c0163f48>] ? sys_init_module+0x88/0x1b0
[  150.770007]  [<c0109f03>] ? sysenter_do_call+0x12/0x2f
[  150.770007]  =======================
[  150.770007] Code: ff 66 c7 85 52 ff ff ff 06 00 89 85 f4 fb ff ff 8d 85 f4 fb ff ff 89 85 24 ff ff ff 90 8d 74 26 00 0f b6 14 0b 8b 85 58 ff ff ff <88> 14 08 83 c1 01 83 f9 06 75 eb 8d 85 24 ff ff ff 89 75 8c c7
[  150.770007] EIP: [<f8f6c722>] ppsc_inquire+0x62/0xa0 [ppscsi] SS:ESP 0068:f2dc7a10
[  150.783457] ---[ end trace 4674ef33ac2d5c80 ]---

```

any ideas?

edit:
i was able to fix the 2 warnings, but did not fix my problem:
> **haydnc said:**
> ```

make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.o
/home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.c: In function &#8216;ppsc_cleanup&#8217;:
/home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.c:849: warning: assignment from incompatible pointer type
/home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.c: In function &#8216;ppsc_detect&#8217;:
/home/haydnc/build/ppscsi/ppscsi-beta2/ppscsi.c:1192: warning: assignment from incompatible pointer type
ppsc.c:849
cmd->sdb.table.sgl = (char *) cmd->sense_buffer;
to
cmd->sdb.table.sgl = (struct scatterlist *) cmd->sense_buffer;

ppsc.c:191
static void ppsc_tq_int (void *data)
to
static void ppsc_tq_int (struct work_struct *data)


> Edit: Confirmed I get that same error message:
[code]FATAL: Error inserting epst (/lib/modules/2.6.31-14-generic/kernel/drivers/parport/epst.ko): No such device
```
Anyone know why? Or anyone out there who found a work around?.
have you enabled the parallel-port in bios? (just be sure)

---

### Post by haydnc on 2009-12-20
Hi tcsoft, which version of Ubuntu are you using?

I know that problems exist with Karmic (because that's what I'm currently on) - no solution so far.

If you're using an older version you'll probably need to hunt back through this thread to find older versions of the code. Unfortunately the solution has changed with each release of Ubuntu so if you've got one of the older versions your best bet is to start at the beginning of the thread and work your way through one solution at a time until you find the one relevant to your current Ubuntu version.

---

### Post by tcsoft on 2009-12-21
i'm using ubuntu 8.10 server. compiling the code works. modprobe fails with a segmentation fault.

---

### Post by haydnc on 2009-12-21
I don't know if it'll work still (with new kernels and everything coming out) but the code fix for getting the 5100C to work in 8.10 was way back on page 1 of this thread. It might be worth giving that a go first.

If that doesn't work you can check back here periodically - hopefully we'll come across something eventually to get ppscsi/epst working under the current kernel.

---

### Post by tcsoft on 2009-12-23
i got it working in 8.10 with some modification (not mentioned in this thread). Now i will try an upgrade to 9.04 and see what happens.

edit:
i'm afraid of installing 9.10 on my production-server because i can't revert to 9.04 again when ppscsi isn't working. so i'll stick with 9.04 until i've found a solution for 9.10. so i'm gonna install 9.10 on my desktop-pc and give ppscsi a try. stay tuned :)

edit2:
yep, 9.04 working too.

---

### Post by tcsoft on 2009-12-24
good news! Just compiled the ppscsi-driver on a ubuntu 9.10 live-cd.
My HP ScanJet 5100C aka HP C5190A works like a charm in 9.10 Karmic Koala. :guitar:

@haydnc
Your problem must have another source - the kernel (2.6.31) is not.

---

### Post by NielsENTP on 2009-12-27
Error when inserting epst:

I am using ubuntu 9.10 and followed the instructions:
tar zxvf ppscsi-beta2-20060424.tar.gz
tar zxvf ppscsi-patch-2_6_27up.tar.gz
mv ppscsi.*.patch ppscsi-beta2
cd ppscsi-beta2
patch -Np1 -i ppscsi.c.patch
patch -Np0 -i ppscsi.h.patch
make
sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
sudo depmod
sudo modprobe ppscsi
sudo modprobe epst

The last command gives me this error:

FATAL: Error inserting epst (/lib/modules/2.6.31-16-generic/kernel/drivers/parport/epst.ko): No such device

and sane-find-scanner does not find the scanner.

I have checked the cable to the scanner and know that the scanner has worked for me under an earlier version of Kubuntu.

Any input on how I can get on with my life is welcome.

Best regards

Niels

PS. I found that "make" does not work if the directory name has a space i.e. my computer downloads by default to "Hentede Filer", so I had to move all files to a different directory to successfully compile the code.

---

### Post by tcsoft on 2009-12-29
for the moment, all i can say is: it works on my system running 9.10 with 2.6.31-16-generic-pae

do you see any errors in "$ dmesg" after inserting epst?

---

### Post by haydnc on 2010-01-02
> **tcsoft said:**
> good news! Just compiled the ppscsi-driver on a ubuntu 9.10 live-cd.
My HP ScanJet 5100C aka HP C5190A works like a charm in 9.10 Karmic Koala. :guitar:

@haydnc
Your problem must have another source - the kernel (2.6.31) is not.

Hi tcsoft,

I'm not sure what we might be doing differently because I just tried again and my machine still doesn't want to successfully complete the sudo modprobe epst command. 

I do get the following in dmesg:
```
[537001.040149] INFO: task modprobe:9425 blocked for more than 120 seconds.
[537001.040159] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[537001.040165] modprobe      D c08145c0     0  9425   7015 0x00000000
[537001.040178]  e3c4fdd8 00200086 e3c4fdd4 c08145c0 d3489bb8 c08145c0 8bcc780d 0001e829
[537001.040193]  c08145c0 c08145c0 d3489bb8 c08145c0 8bc8342d 0001e829 c08145c0 ea889c00
[537001.040206]  d3489920 08022bdd e3c4fdf4 f7070000 e3c4fe34 c056f6da c0318759 e3c4fdec
[537001.040220] Call Trace:
[537001.040240]  [<c056f6da>] schedule_timeout+0x12a/0x200
[537001.040250]  [<c0318759>] ? __delay+0x9/0x10
[537001.040261]  [<c0150510>] ? process_timeout+0x0/0x10
[537001.040270]  [<c056f7c5>] schedule_timeout_uninterruptible+0x15/0x20
[537001.040278]  [<c0150cd5>] msleep+0x15/0x20
[537001.040291]  [<f861a4a4>] ppsc_reset_pha+0x34/0x90 [ppscsi]
[537001.040301]  [<f861a79f>] ppsc_test_mode+0xff/0x1a0 [ppscsi]
[537001.040311]  [<c022e0c3>] ? proc_mkdir_mode+0x33/0x50
[537001.040318]  [<c022e0ef>] ? proc_mkdir+0xf/0x20
[537001.040329]  [<c03c0122>] ? scsi_proc_hostdir_add+0x32/0x70
[537001.040339]  [<c03b3f6d>] ? scsi_host_alloc+0x23d/0x2b0
[537001.040347]  [<c03b7a50>] ? scsi_error_handler+0x0/0x130
[537001.040355]  [<c03b3ff3>] ? scsi_register+0x13/0x70
[537001.040365]  [<f861b2f9>] ppsc_detect+0x449/0x5b0 [ppscsi]
[537001.040374]  [<f861a310>] ? ppsc_wake_up+0x0/0xc0 [ppscsi]
[537001.040417]  [<c01d39de>] ? vfree+0x1e/0x30
[537001.040427]  [<f81c5015>] epst_detect+0x15/0x20 [epst]
[537001.040435]  [<f818b05f>] init_this_scsi_driver+0x5f/0xcc [epst]
[537001.040444]  [<c010112c>] do_one_initcall+0x2c/0x190
[537001.040452]  [<f818b000>] ? init_this_scsi_driver+0x0/0xcc [epst]
[537001.040462]  [<c0173751>] sys_init_module+0xb1/0x1f0
[537001.040469]  [<c010336c>] syscall_call+0x7/0xb

```

Any ideas I am running the 32 bit Karmic with kernel 2.6.31-16-generic. As before it just hangs when trying to install epst - no indication of why. Did you need to do anything that wasn't laid out in this thread? I'm willing to give anything a go, though I would obviously rather not reinstall.

Actually, that could be the difference. Is your Karmic install a clean install or an upgrade from 9.04? I think I might've upgraded instead of doing a clean install this time (can't recall), so if that turns out to be the only difference let me know and I'll give it a go.
:)

---

### Post by kebajonathan on 2010-01-03
I made a clean install, but loading epst still hangs. I guess it's because the detection of the device (in ppscsi.ko) doesn't work as it should:

CC [M]  /home/xxx/ppscsi-beta2/ppscsi.o
/home/xxx/ppscsi-beta2/ppscsi.c: In function ‘ppsc_cleanup’:
/home/xxx/ppscsi-beta2/ppscsi.c:849: warning: assignment from incompatible pointer type
/home/xxx/ppscsi-beta2/ppscsi.c: In function ‘ppsc_detect’:
/home/xxx/ppscsi-beta2/ppscsi.c:1192: warning: assignment from incompatible pointer type

---

### Post by tcsoft on 2010-01-05
I've upped a new patch on my [blog]("http://infabo.net/linux/ubuntu/how-i-got-my-hp-scanjet-5100c-working-under-ubuntu.html").

---

### Post by kebajonathan on 2010-01-05
It (HP Scanjet 5100c) works (even on gentoo, kernel 2.6.32). I get a compile error though (works anyway, but I just wanted to inform you:
make -C /lib/modules/`uname -r`/build M=`pwd` modules                             
make[1]: entrant dans le répertoire « /usr/src/linux-2.6.32-tuxonice »            
  CC [M]  /home/xxx/ppscsi-beta2/ppscsi.o             
/home/xxx/ppscsi-beta2/ppscsi.c: In function ‘ppsc_detect’:
/home/xxx/ppscsi-beta2/ppscsi.c:1192: attention : assignment from incompatible pointer type

Anyway, thanks again

---

### Post by haydnc on 2010-01-06
Thanks tcsoft, I'll give your updated version a go tonight. If it works do you mind if I post the instructions here as well (for those who're too lazy to follow your link ;))?

---

### Post by haydnc on 2010-02-02
A copy of the ppscsi build files with all current patches applied can be downloaded from [here]("http://homepages.woosh.co.nz/gryphon/files/ppscsi-patched-karmic.tar.gz").

Once you've got it run the following commands:
```

tar -zxvf ppscsi-patched-karmic.tar.gz
cd ppscsi-beta2
sudo make
sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
sudo depmod -a
sudo modprobe ppscsi
sudo modprobe epst

```

Assuming your scanner works after this point you probably should add ppscsi and epst to /etc/modules

You can do this by typing the following at your command prompt:
```

sudo gedit /etc/modules

```
Add ppscsi and epst, each should be on its own line at the end of the file.
Save and exit modules. 

Obviously you don't need to use gedit - whatever editor you prefer will do the trick. This does work on Ubuntu Karmic 9.10.

As usual, thanks to tcsoft and everyone else who helped us get this far. Hopefully things will keep working in the next release...

---

### Post by messelink on 2010-03-13
Excellent work everyone, much appreciated info. Especially haydnc, coordinating as always.

On a side note, since I installed my scanner again it makes a grinding noise after acquiring a preview and returning to the start position. Can it be driver related or is it just getting old?

---

### Post by haydnc on 2010-03-14
I'm not entirely certain what you mean by a grinding sound but I do know that my 5100C has always been a bit of a noisy beast from day one.

Particularly when I'm trying to scan at high resolutions. It is definitely **not** quiet.

I do hate to say it though, about the only way you'll ever really be able to tell if it's drivers or age is to hook it up to an old windows box and see if you get the same noise running the scanner off linux.

Personally, I'm not *that* interested in finding out the answer with regards to my scanner. ;)
It's up to you how keen you are to find out for yours.

---

### Post by kebajonathan on 2010-03-29
**An important not from the [gentoo forums]("http://forums.gentoo.org/viewtopic-p-6223070.html#6223070") for kernel 2.6.33:**

/usr/src/linux/include/linux/autoconf.h was moved to /usr/src/linux/include/generated/autoconf.h
As a result, in ppscsi.h, change

```
#include <linux/autoconf.h>
```

to

```
#include <generated/autoconf.h>
```

---

### Post by haydnc on 2010-03-29
I've just done a test build of the ppscsi code (linked to above) as is without any modifications on a test Ubuntu 10.04 box and it seems to work without any changes.

That is probably because even the beta release is still on the 2.6.32 kernel.

I'm not going to change anything at this point, because it might break things for Ubuntu users who're trying to use this code. 

However if there is anyone out there who is using a 2.6.33 kernel and is having trouble, the change provided by kebajonathan can be made on line 16 of the ppscsi.h file.

We'll just have to wait and see if the location of autoconf.h changes when Ubuntu reaches the 2.6.33 kernel.

---

### Post by messelink on 2010-04-11
The noise is definitely different, it sounds like two gear wheels slipping over each other. It is not in locked mode so it shouldn't be that. Seems I will have to take it apart. Shame it served me well over the years and I'm gonna miss you guys if I have to get another. =P

---

### Post by haydnc on 2010-04-30
So, Lucid (10.04) is here...
I've upgraded and for the first time ever these instructions still work with the installation of a new version of Ubuntu!

Never thought I'd see the day.

The only changes are not ppscsi related. First: they've removed the install of xsane as default (don't know about the rest of you, that's what I was using to scan with).

That can be easily fixed by a simple sudo apt-get intall xsane, or installing xsane from inside Synaptic.

The other 'change' is that I lost the hosting where I previously had the link to the patched ppscsi file, which is a bit of a pain.

When I find a reliable and secure place to put it, I'll post a new link in here for ease of download. If you're desperate for a copy let me know and I'll try do it faster.

Update: New download location [here]("http://homepages.woosh.co.nz/gryphon/files/ppscsi-patched-karmic.tar.gz"). 
MD5SUM: 40d48f89c992cb10015ff86607564dd9  ppscsi-patched-karmic.tar.gz

---

### Post by tcsoft on 2010-04-30
> **kebajonathan said:**
> It (HP Scanjet 5100c) works (even on gentoo, kernel 2.6.32). I get a compile error though (works anyway, but I just wanted to inform you:
make -C /lib/modules/`uname -r`/build M=`pwd` modules                             
make[1]: entrant dans le répertoire « /usr/src/linux-2.6.32-tuxonice »            
  CC [M]  /home/xxx/ppscsi-beta2/ppscsi.o             
/home/xxx/ppscsi-beta2/ppscsi.c: In function &#8216;ppsc_detect&#8217;:
/home/xxx/ppscsi-beta2/ppscsi.c:1192: attention : assignment from incompatible pointer type

Anyway, thanks again
that's just a warning - cosmetics. function expects void and gets a different type.

and yeah - still works in 10.04 without changes! :guitar:

---

### Post by Younio on 2010-05-12
Hi again, 

So here is how it is, I have been having problems with upgrading from 9.10 to 10.04 with graphics, so i did a clean install. So now I'm on lucid. And when i fallow commands provided by tcsoft, everything goes well until command > sudo modprobe epst

 i still get the same error as in karmic: 
> FATAL: Error inserting epst (/lib/modules/2.6.32-22-generic/kernel/drivers/parport/epst.ko): No such device



By the way, I didn't try these commands in karmic, didn't knew they were here :confused:

Hope someone can help me.

---

### Post by tcsoft on 2010-05-12
not the ppscsi/epst-driver is your problem, your kernel does not detect your parallel-port (parport). maybe your parport has to be enabled in bios, set to ECP.

---

### Post by Kralnor on 2010-06-03
Windows 7 doesn't have support for the 5100C so it's back to Ubuntu for scanning at least ;) I had to use a Live CD back from the Edgy era in order to be able to scan, but getting it running on Lucid would of course be much nicer.

However, it seems that once again I have trouble with ppscsi.

> **haydnc said:**
> A copy of the ppscsi build files with all current patches applied can be downloaded from [here]("http://homepages.woosh.co.nz/gryphon/files/ppscsi-patched-karmic.tar.gz").

Once you've got it run the following commands:
```

tar -zxvf ppscsi-patched-karmic.tar.gz
cd ppscsi-beta2
sudo make
sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
sudo depmod -a
sudo modprobe ppscsi
sudo modprobe epst

```


I tried the above, but once I run 'sudo make' I get the following error:

```

make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: *** No rule to make target `filer/ppscsi-beta2'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [all] Error 2

```

What gives? I have already run 

```

sudo apt-get install build-essential linux-headers-`uname -r`

```

---

### Post by haydnc on 2010-06-07
Hi Kralnor,

I'm not sure what's gone wrong for you there.

I've just done another test build to check that the patched version of the files still work and they definitely do.

I used a clean install of Lucid with current updates and build-essential installed to do the test and it compiled without any issues.

Interestingly enough you don't need to put sudo in front of the 'make' but you should for everything else (as above).

Were you working with an upgraded version of Lucid or a clean install? Were you patched up to date (not that it should make much difference)? Also have you tried forcing a re-install of build-essential with all its dependencies? It could be that somehow something was either left out of your install or got corrupted during install.

Good luck getting it to work.

---

### Post by tcsoft on 2010-06-08
@Kralnor
maybe you've got whitespaces in your workingpath. pwd does not add escape characters.
open the Makefile and look for ```
M=`pwd`
``` and change it to ```
M=`pwd | sed -e 's/\ /\\\ /g'`
```

---

### Post by Kralnor on 2010-06-08
Whitespaces were indeed the root of the problem, although changing the assignment to M as described did not help. I just ended up using a path without whitespaces and now I can scan in Lucid ;)

Thanks!

---

### Post by haydnc on 2011-02-27
Has anyone tried this out on 10.10 yet. I keep meaning to, but I've not gotten around to it.

---

### Post by haydnc on 2011-03-04
Well to answer my own question, no. This does not work in 10.10.

The linked (patched version) of ppscsi doesn't compile at all. If you make the change suggested a page back for the 2.6.33+ kernel - specifically changing line 16 of ppscsi.h **from** #include <linux/autoconf.h> **to** #include <generated/autoconf.h> it does compile - but the scanner is still not detected after the 'sudo depmod -a' and the 'sudo modprobe ppscsi / epst'.

Short version: if you're still relying on your old 5100C don't upgrade from 10.04 LTS at this stage.

If anyone has any ideas what's gone wrong this time and/or you've got your scanner working on 10.10 let me know.

If you gave up and just got a new scanner let me know what it is that you brought that works. ;)

---

### Post by haydnc on 2011-05-08
I notice that there hasn't been any movement on this thread since before 10.10 came out and we're now into the era of 11.04 so I guess maybe it is time to mark this thread as closed/dead.

I have finally ditched my old HP Scanjet 5100C in favour of a new Canon CanoScan LiDE 110 which works perfectly well out of the box with current versions of Ubuntu. 

Best of luck for anyone wanting to keep their 5100C alive but it is time for me to move on into the realm of more up-to-date hardware.

If you're considering the purchase of a new scanner and you're unsure if it'll work in linux I suggest very strongly you check out the list of SANE compatible devices that can be found here: [http://www.sane-project.org/sane-mfgs.html#SCANNERS]("http://www.sane-project.org/sane-mfgs.html#SCANNERS"). There is quite a large list of scanners there these days and they're clearly labelled which ones work and which ones don't. 

I hit the websites for my local hardware suppliers and checked the scanners that they had available then compared it to the list of compatible scanners and found one that I could afford that was on the list of **working** scanners.

---

### Post by kebajonathan on 2011-05-09
Short answer: The scanner still works. At least on Gentoo. I think it might on 10.10, but since I skipped this release and I'm kind of busy working , I haven't gotten to test it on 11.04 yet. 

For the gentoo thread: [http://forums.gentoo.org/viewtopic-t-175465-postdays-0-postorder-asc-highlight-5100c-start-75.html]("http://forums.gentoo.org/viewtopic-t-175465-postdays-0-postorder-asc-highlight-5100c-start-75.html")

---

### Post by haydnc on 2011-05-09
Hi kebajonathan, I did test my 5100C when I was using 10.10 and while the ppscsi code compiled and the modules appeared to load for reasons I don't understand my scanner refused to function. 

If others have managed to get it working on 10.10 and it was just me having bad luck, well let's just say it wouldn't be the first time I've had random things go wrong after an upgrade.

As it happens for the first time in a very long time I had some money that I could call spare and I discovered that there were some very reasonably priced flatbed scanners on the SANE 'working' list so I decided to give up on the ongoing fight to keep my old parallel port scanner working and move on to a fully supported USB one. I also gave away the old scanner so I don't even have it for testing purposes any more which in hindsight is kind of sad, but it is much too late now.

I guess there are probably still some people out there trying to keep the 5100C working in 10.10 or even 11.04, it's just that this thread used to see a fairly large number of posts following each new release and it went utterly quiet around the time 10.10 came out. 

It seemed like a logical assumption to make that since it hadn't worked at all for me since 10.04 that most of the regular visitors had given up and moved on to a friendlier low cost replacement.

If you do manage to get your 5100C working successfully under 11.04 and you've time to post that confirmation here I guess there are probably people out there who'd love to know about it.
:)

---

### Post by kebajonathan on 2011-05-18
So the problem is this code:

```
struct scsi_host_template   driver_template = PPSC_TEMPLATE(onscsi);
```

in t348.c:302, t358.c:378, onscsi.c:529, epsa2.c:492, epst.c:463, vpi0.c:261 and sparcsi.c:373 because it's (apparently) an "initialization from incompatible pointer type". This structure is declared in /usr/src/linux/include/scsi/libiscsi.h, /usr/src/linux/include/scsi/scsi_host.h and /usr/src/linux/drivers/scsi/scsi_priv.h

When loading the modules, it produces a kernel panic, which explains the system freeze that can occur.

I don't know how to fix this, as I'm no C programmer, but maybe someone here knows? That would be a great help...

---

### Post by blwh on 2011-06-01
I recently upgraded directly to Ubuntu 11.04 (Natty) from Ubuntu 10.04 (Lucid) and then started debugging this code as it no longer worked.  I have a diff from ppscsi-patched-karmic.tar.gz posted by haydnc that compiles without errors or warnings for Ubuntu 11.04 (other than the stack frame bytes exceeding 1024 in function ppsc_inquire).

$ diff ppscsi-beta2-karmic/ ppscsi-beta2-natty/
diff ppscsi-beta2-karmic//ppscsi.c ppscsi-beta2-natty//ppscsi.c
191c191
< static void ppsc_tq_int (void *data)
---
> static void ppsc_tq_int (struct work_struct *data)
386c386
< int ppsc_queuecommand (struct scsi_cmnd *cmd, void (*done)(struct scsi_cmnd *))
---
> int ppsc_queuecommand (struct Scsi_Host *host, struct scsi_cmnd *cmd)
388c388
<     PHA *pha = (PHA *) cmd->device->host->hostdata[0];
---
>     PHA *pha = (PHA *) host->hostdata[0];
396c396
<     pha->done = done;
---
>     pha->done = cmd->scsi_done;
1045d1044
< 
1235c1234
<         hreg->unique_id = (int) pha; /* What should we put in here??? */
---
>         hreg->unique_id = (unsigned long)pha; /* What should we put in here??? */
diff ppscsi-beta2-karmic//ppscsi.h ppscsi-beta2-natty//ppscsi.h
16c16
< #include <linux/autoconf.h>
---
> #include <generated/autoconf.h>
35c35
< extern int ppsc_queuecommand(struct scsi_cmnd *, void (* done)(struct scsi_cmnd *));
---
> extern int ppsc_queuecommand(struct Scsi_Host *, struct scsi_cmnd *);

Although this diff patch compiles correctly for kernel 2.6.37 and above it still does not function correctly and it is not compatible with kernel 2.6.36 or lower due to the change in queuecommand for the structure scsi_host_template in the file /usr/src/linux/include/scsi/scsi_host.h, which is where the major difference is between Ubuntu 10.10 (maverick) and Ubuntu 11.04 (natty).  In theory, the code modifications should work but fails to find the  scanner in Simple Scan as it did in 10.04 (Lucid).  I've since back  tracked to Ubuntu 10.10 (maverick) and found that the kernel version for  that distro does not work either even though the diff changes are  very simple requiring only the path to autoconf.h to change.  I am guessing  whatever failed in 10.10 (maverick) is also the same problem with 11.04  (natty), if these diffs I've provided are correct.  In summary, kernel  2.6.37 involves changes  to queuecommand with the scsi done() callback and has reduced  the pointer dereferencing of the host parameter by passing a separate  argument.

[http://lxr.free-electrons.com/source/include/scsi/scsi_host.h?v=2.6.36](http://lxr.free-electrons.com/source/include/scsi/scsi_host.h?v=2.6.36)
[http://lxr.free-electrons.com/source/include/scsi/scsi_host.h?v=2.6.37](http://lxr.free-electrons.com/source/include/scsi/scsi_host.h?v=2.6.37)

The following macro in ppscsi.h for queuecommand is the source of error for kernel 2.6.37 or Ubuntu 11.04 (natty):

```
#define PPSC_TEMPLATE(proto){               \
    .name =            #proto,              \
    .detect =             proto##_detect,    \
    .release =        ppsc_release,      \
    .proc_name =        #proto,           \
    .proc_info =          ppsc_proc_info,    \
    .queuecommand =       ppsc_queuecommand, \
    .eh_abort_handler =    ppsc_abort,       \
    .eh_bus_reset_handler =   ppsc_reset,       \
    .eh_host_reset_handler =  ppsc_reset,       \
    .bios_param =         ppsc_biosparam,    \
    .can_queue =          1,                \
    .sg_tablesize =       SG_NONE,           \
    .cmd_per_lun =        1,                 \
    .use_clustering =     DISABLE_CLUSTERING \
}

```Documentation on queuecommand discusses changes on the arguments and locking mechanism:
[http://www.kernel.org/doc/Documentation/scsi/scsi_mid_low_api.txt](http://www.kernel.org/doc/Documentation/scsi/scsi_mid_low_api.txt)

Here are the 2.6.37 release candidate changes for SCSI queuecommand and many drivers effected by that change (search 'done' in your browser to see the relevant changes):
[http://www.gossamer-threads.com/lists/linux/kernel/1301610](http://www.gossamer-threads.com/lists/linux/kernel/1301610)

Isolating the exact kernel version (somewhere between 2.6.32 and 2.6.35) that caused this code to stop functioning would be a good starting point so that the kernel differences and documentation can be analysed.  I have verified 2.6.32 to work as expected and would like to know which version it stopped working under (2.6.33 or 2.6.34 since 2.6.35 doesn't seem to work).  Debugging this code is very time consuming so if anyone else has input at this point it would be useful.

Thanks for all the previous work that allowed the HP Scanjet 5100C to operate under Ubuntu 10.04 (lucid)

---

### Post by kebajonathan on 2011-06-02
I would help if I could, but I have no idea how to fix this. At least there is no kernel panic any more.

The problem seems to be that the scanner does not get recognized... I'm sorry, I'm no programmer...

---

### Post by blwh on 2011-06-03
I updated Ubuntu 10.04 to the latest supported kernel which is 2.6.32-32-generic and the scanner works fine.  I also have Ubuntu 10.10 Beta which is using kernel version 2.6.35-19-generic while the official release of Ubuntu 10.10 shipped with 2.6.35-22-generic.  There does not appear to be an Ubuntu release that ever used 2.6.33 or 2.6.34 versions of the kernel and the scanner stopped working somewhere along this transition.

I will research the kernel differences as relates to the scsi driver and try to enable verbose diagnostics of the patched code being used on this forum.  I have enough coding experience to understand the driver and I believe the problem is early on during the initialisation stage.  The book, "Essential Linux Device Drivers" by Sreekrishnan Venkateswaran from Prentice Hall has several examples using the parallel port and scsi block drivers and some good advice on debugging.  I'll try my best to gain some insight on the problem and report back.

I have a vested interest in getting the driver working again as I've recently purchased a special ordered compact PCI Express Parallel Port Adaptor for my Gigabyte EX-58 Extreme motherboard with i7-980 hex core that fits right beside the CPU cooler in a tight spot that most adaptors won't fit.  It was all a gamble to see if I could use the scanner with Ubuntu - it worked and now I want to keep using it!

[http://www.startech.com/product/PEX1P-1-Port-EPP-ECP-PCI-Express-Parallel-Card-](http://www.startech.com/product/PEX1P-1-Port-EPP-ECP-PCI-Express-Parallel-Card-)

---

### Post by kebajonathan on 2011-06-16
I thought I'd try again in kernel 2.6.39, and here is what I get:
```

user@dhcppc5 ~/ppscsi-beta2 $ make
make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: entrant dans le répertoire « /usr/src/linux-2.6.39-pf2 »
  CC [M]  /home/user/ppscsi-beta2/ppscsi.o
/home/user/ppscsi-beta2/ppscsi.c:73: erreur: &#8216;SPIN_LOCK_UNLOCKED&#8217; undeclared here (not in a function)
make[2]: *** [/home/user/ppscsi-beta2/ppscsi.o] Erreur 1
make[1]: *** [_module_/home/user/ppscsi-beta2] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-2.6.39-pf2 »
make: *** [all] Erreur 2

```
Obviously, you'll not be interested in this kernel (yet) because it will probably only be in the next Ubuntu release (unless kernel 3.0 makes it in there), but if you find out how to solve this problem, I'd be very much interested.

---

### Post by hwertz on 2011-10-31
After looking at a little discussion here, [http://http://forums.gentoo.org/viewtopic-p-6858304.html]("http://http://forums.gentoo.org/viewtopic-p-6858304.html") it appeared the remaining patches to get the 5100C going were not too extensive.  Compared to the patch already in this thread, it actually was just reverting two lines of the patch, and patching a couple other lines -- ppsc_queuecommand in 2.6.37+ runs with no locks and interrupts enabled, which won't work for something like a parallel port where timing is so important.  Renaming this function ppsc_queuecommand_lck and adding one line makes the scsi layer wrap an IRQ disable/enable around this call like it used to -- resulting in a working driver again.  VERIFIED WORKING ON Ubuntu 11.04 -- 2.6.38-11-generic kernel! :D

     This patch incorporates the patch to make the driver build cleanly against 2.6.37, so this goes directly against ppscsi-patched-karmic.tar.gz :popcorn:  :
```
diff -cr ppscsi-beta2/ppscsi.c ppscsi-beta2-updated/ppscsi.c
*** ppscsi-beta2/ppscsi.c	2010-01-06 18:47:53.000000000 -0600
--- ppscsi-beta2-updated/ppscsi.c	2011-10-31 14:15:02.000000000 -0500
***************
*** 188,194 ****
  	spin_unlock_irqrestore(&ppsc_spinlock,flags);
  }
  
! static void ppsc_tq_int (void *data)
  {
  	void (*con)(PHA *);
  	unsigned long flags;
--- 188,194 ----
  	spin_unlock_irqrestore(&ppsc_spinlock,flags);
  }
  
! static void ppsc_tq_int (struct work_struct *data)
  {
  	void (*con)(PHA *);
  	unsigned long flags;
***************
*** 383,389 ****
  	return cmd->result;
  }
  
! int ppsc_queuecommand (struct scsi_cmnd *cmd, void (*done)(struct scsi_cmnd *))
  {
  	PHA *pha = (PHA *) cmd->device->host->hostdata[0];
  
--- 383,389 ----
  	return cmd->result;
  }
  
! int ppsc_queuecommand_lck (struct scsi_cmnd *cmd, void (*done)(struct scsi_cmnd *))
  {
  	PHA *pha = (PHA *) cmd->device->host->hostdata[0];
  
***************
*** 393,405 ****
  	}
  
  	pha->cur_cmd = cmd;
! 	pha->done = done;
  	pha->then = jiffies;
  
  	ppsc_do_claimed(pha,ppsc_start);
  
  	return 0;
  }
  
  static void ppsc_arb_fail (PHA *pha)
  {
--- 393,407 ----
  	}
  
  	pha->cur_cmd = cmd;
!     pha->done = cmd->scsi_done;
  	pha->then = jiffies;
  
  	ppsc_do_claimed(pha,ppsc_start);
  
  	return 0;
  }
+ DEF_SCSI_QCMD(ppsc_queuecommand)
+ 
  
  static void ppsc_arb_fail (PHA *pha)
  {
***************
*** 1232,1238 ****
  		hreg = scsi_register(tpnt,sizeof(PHA*));
  		hreg->dma_channel = -1;
  		hreg->n_io_port = 0;
! 		hreg->unique_id = (int) pha; /* What should we put in here??? */
  		hreg->sg_tablesize = s;
  		hreg->hostdata[0]=(unsigned long)pha; /* Will be our pointer */
  
--- 1234,1240 ----
  		hreg = scsi_register(tpnt,sizeof(PHA*));
  		hreg->dma_channel = -1;
  		hreg->n_io_port = 0;
!        hreg->unique_id = (unsigned long)pha; /* What should we put in here??? */
  		hreg->sg_tablesize = s;
  		hreg->hostdata[0]=(unsigned long)pha; /* Will be our pointer */
  
diff -cr ppscsi-beta2/ppscsi.h ppscsi-beta2-updated/ppscsi.h
*** ppscsi-beta2/ppscsi.h	2010-01-06 18:47:53.000000000 -0600
--- ppscsi-beta2-updated/ppscsi.h	2011-10-31 15:56:35.000000000 -0500
***************
*** 13,19 ****
  #define	PPSC_H_VERSION	"0.92"
  
  #include <linux/module.h>
! #include <linux/autoconf.h>
  #include <linux/version.h>
  #include <linux/stddef.h>
  #include <linux/types.h>
--- 13,19 ----
  #define	PPSC_H_VERSION	"0.92"
  
  #include <linux/module.h>
! #include <generated/autoconf.h>
  #include <linux/version.h>
  #include <linux/stddef.h>
  #include <linux/types.h>
***************
*** 32,38 ****
  
  extern int ppsc_proc_info(struct Scsi_Host *, char *,char **,off_t,int,int);
  extern int ppsc_command(struct scsi_cmnd *);
! extern int ppsc_queuecommand(struct scsi_cmnd *, void (* done)(struct scsi_cmnd *));
  extern int ppsc_abort(struct scsi_cmnd *);
  extern int ppsc_reset(struct scsi_cmnd *);
  extern int ppsc_biosparam(struct scsi_device *, struct block_device *, sector_t capacity, int[]);
--- 32,38 ----
  
  extern int ppsc_proc_info(struct Scsi_Host *, char *,char **,off_t,int,int);
  extern int ppsc_command(struct scsi_cmnd *);
! extern int ppsc_queuecommand(struct Scsi_Host *shost, struct scsi_cmnd *cmd);
  extern int ppsc_abort(struct scsi_cmnd *);
  extern int ppsc_reset(struct scsi_cmnd *);
  extern int ppsc_biosparam(struct scsi_device *, struct block_device *, sector_t capacity, int[]);
```

     And to avoid the inevitable mangling of whitespace and such from cut-n-paste, it's also attached.  Had to gzip it since the forum won't take a .patch file but will take a .patch.gz.

---

### Post by hwertz on 2011-11-01
A few more items to make it nice:
     This was on an earlier page, to fix the permissions problems the scanner has by default so xsane and such don't have to be run as root.  This is in /etc/udev/rules.d/45-libsane.rules:
```

SUBSYSTEM=="scsi_generic",ATTRS{type}=="3", NAME="%k", SYMLINK="scanner%n", MODE="0777", GROUP="scanner"

```

     Secondly, Ubuntu has plenty of kernel updates, and who wants to remember to rebuild ppscsi each time?  Make runs very fast when there's nothing to build, and ~30 seconds (on a pretty antiquated box) when it does.  So I stuck this in /etc/rc.local just before the "exit 0":
```

(cd /usr/src/ppscsi-beta2/
 make
 insmod ./ppscsi.ko
 insmod ./epst.ko) 

```
     Rebuilds ppscsi if needed, and loads the modules.

---

### Post by kebajonathan on 2011-11-01
Well, I'm attaching a patch for kernel 3.0.x. For more details, head over to the [Gentoo forums]("http://forums.gentoo.org/viewtopic-p-6859438.html#6859438").

---

### Post by crockysam on 2011-11-07
> **kebajonathan said:**
> Well, I'm attaching a patch for kernel 3.0.x. For more details, head over to the [Gentoo forums]("http://forums.gentoo.org/viewtopic-p-6859438.html#6859438").

Hi,

I tried this on the latest Ubuntu (3.0.0-12-generic kernel) and gives me the following error at the end:

```
> modprobe epst
FATAL: Error inserting epst (/lib/modules/3.0.0-12-generic/kernel/drivers/parport/epst.ko): No such device

```

Did the patching as you mentioned in the post.

---

### Post by haydnc on 2012-02-24
FWIW I finally got rid of my 5100C and picked up a Canon LIDE 110 which works out of the box. 

Unfortunately this means I'm no longer able to test the ppscsi patches etc.

Sorry folks. Best of luck to those of you still struggling on with the old parallel port scanner.
):P

---

### Post by tcsoft on 2012-05-11
> **crockysam said:**
> Hi,

I tried this on the latest Ubuntu (3.0.0-12-generic kernel) and gives me the following error at the end:

```
> modprobe epst
FATAL: Error inserting epst (/lib/modules/3.0.0-12-generic/kernel/drivers/parport/epst.ko): No such device

```Did the patching as you mentioned in the post.

same here at 12.04 / kernel 3.2.0

---

### Post by Kralnor on 2012-11-24
> **kebajonathan said:**
> Well, I'm attaching a patch for kernel 3.0.x. For more details, head over to the [Gentoo forums]("http://forums.gentoo.org/viewtopic-p-6859438.html#6859438").

Following the instructions posted by keba worked for me in Ubuntu 12.04, running kernel 3.2.x. Thanks!

This 5100C is still going strong :)

---

### Post by tcsoft on 2012-11-24
> **Kralnor said:**
> This 5100C is still going strong :)

For sure, here too! 12.04 still working!

---

### Post by nedw on 2013-01-03
Hello all.  I'm a newbie here and, having inherited a HP 5100C, I wanted to try and get it working under 12.04 / kernel 3.2.0-33.  My intention was to follow keba's instructions and apply ppscsi-3.0.patch.zip against ppscsi-patched-karmic.tar.gz.

However, the link [http://homepages.woosh.co.nz/gryphon/files/ppscsi-patched-karmic.tar.gz](http://homepages.woosh.co.nz/gryphon/files/ppscsi-patched-karmic.tar.gz), which is mentioned several times in the thread, appears to be broken.

Does anyone have a link to, or copy of ppscsi-patched-karmic.tar.gz  ?

Thanks for any help.

P.S. After failing to find ppscsi-patched-karmic.tar.gz myself, I thought I would start from scratch with ppscsi-beta2-20060424.tar.gz and work my way through this thread and the associated Gentoo thread applying all the relevant patches.  I got as far as getting ppscsi to compile but, upon loading epst, I get a kernel panic when the 5100C is attached.  Thanks again.

---

### Post by zdenek archlinux on 2013-03-15
Hi

Im a novice on this forum. I doesnt use Ubuntu at all, but i think that i have a important message.

Scanner  HP Scanjet 5100C works fine on Linux 3.7.10. Now is 15.3.2013 - scanner is 9 year old.

Because many of old patches is today unavailable (like ppscsi-patched-karmic.tar.gz) here is complete driver for kernel 3.7.10.

[http://www.zdenek-stepanek.eu/ppscsi-beta2-3.7.10.tar.gz](http://www.zdenek-stepanek.eu/ppscsi-beta2-3.7.10.tar.gz)

Please understand that I'm not a programmer. Driver above is only original driver (ppscsi-beta2-20060424.tar.gz) with all patchsets, which I found on this and other forums.



Goog luck :-)

---

### Post by nedw on 2013-03-16
Hi,
Thank you very much for that - I appreciate it.  I'll give it a try (when I get time) and post if I get it working.  I inherited the scanner from someone who was throwing it out, so I thought I'd give it a try on Linux to see if I could get it working before consigning it to the scrap heap.  Thanks again!

---

### Post by Kralnor on 2013-05-03
> **zdenek archlinux said:**
> Hi

Im a novice on this forum. I doesnt use Ubuntu at all, but i think that i have a important message.

Scanner  HP Scanjet 5100C works fine on Linux 3.7.10. Now is 15.3.2013 - scanner is 9 year old.

Because many of old patches is today unavailable (like ppscsi-patched-karmic.tar.gz) here is complete driver for kernel 3.7.10.

[http://www.zdenek-stepanek.eu/ppscsi-beta2-3.7.10.tar.gz](http://www.zdenek-stepanek.eu/ppscsi-beta2-3.7.10.tar.gz)

Please understand that I'm not a programmer. Driver above is only original driver (ppscsi-beta2-20060424.tar.gz) with all patchsets, which I found on this and other forums.



Goog luck :-)

Doesn't seem to work for me. When I do the standard

```

sudo make
sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
sudo depmod -a
sudo modprobe ppscsi
sudo modprobe epst

```

I get this error

```

FATAL: Error inserting ppscsi (/lib/modules/3.2.0-40-generic-pae/kernel/drivers/parport/ppscsi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

at

```

sudo modprobe ppscsi

```

The relevant output from dmesg seems to be

```

[  969.129677] ppscsi: Unknown symbol parport_register_device (err 0)
[  969.129688] ppscsi: Unknown symbol parport_register_driver (err 0)
[  969.129696] ppscsi: Unknown symbol parport_release (err 0)
[  969.129704] ppscsi: Unknown symbol parport_claim (err 0)
[  969.129716] ppscsi: Unknown symbol parport_unregister_device (err 0)
[  969.129729] ppscsi: Unknown symbol parport_unregister_driver (err 0)
[  969.129745] ppscsi: Unknown symbol parport_put_port (err 0)

```

---

### Post by tcsoft on 2013-05-05
which kernel?

---

### Post by Kralnor on 2013-05-05
Running 'uname -r' gave the following:

```

3.2.0-40-generic-pae

```

However, I since updated to 3.2.0-41-generic-pae and now it works without a hitch, following the instructions outlined in my previous post.

Odd, but no complaints from me :)

---

### Post by nedw on 2013-05-16
I installed the ppscsi-3.7.10.tar.gz posted by zdenek (thanks) on my 12.04 system with 3.2.0-41 kernel, but it was initially giving a kernel panic in "ppsc_inquire".  After a little investigation, I managed to fix it (it was an uninitialised structure member) and have attached the required patch.

To document what I did in case it's useful to someone:

```
sudo make
sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
sudo depmod -a
sudo modprobe ppscsi
sudo modprobe epst
```
The "modprobe epst" gave a "no such device" error when the scanner was not plugged in.  When the scanner was plugged in, the command took about 45 seconds to complete.  Doing a "dmesg" then showed the following:

```

[  955.965635] ppSCSI 0.92 (0.92) installed
[ 1000.652033] epst.0: epst 0.92 (0.92), Shuttle EPST at 0x378 mode 5 (EPP-32) dly 1 nice 0 sg 16
[ 1000.652038] scsi6 : epst
[ 1000.684221] scsi 6:0:0:0: Processor         HP       C5190A           3740 PQ: 0 ANSI: 2
[ 1001.325034] scsi 6:0:0:0: Attached scsi generic sg2 type 3
```

To find the scanner and start a scan:

```

$ sudo sane-find-scanner
...
found SCSI processor "HP C5190A 3740" at /dev/sg2
...
$ sudo scanimage -d hp:/dev/sg2 --mode Color > hpscan
```
It takes about a minute before anything starts happening.  The scan head doesn't move in a continuous motion, but seems to scan for a second or so, then hitch back part way, then start scanning again etc - in a kind of "two steps forward one step back" kind of motion.  The results from the scan are fine though.  I figure the scan data isn't being pulled from the scanner fast enough, as when I tried setting the scanimage resolution down to 100dpi, the scan proceeded smoothly in one motion without this hitch back behaviour.

I get the above results when setting the parallel port into "EPP" mode in the BIOS.  When I tried "ECP" (and, for that matter "EPP+ECP") modes, then I got the same scanning behaviour, but there was a now a noticeable pause when skipping backwards, such that the scan took considerably longer to complete.  I left the port in EPP mode for the fastest scan - not sure if that's just my system or more generally applicable.  My motherboard is a Gigabyte Z77M-D3H.

---

