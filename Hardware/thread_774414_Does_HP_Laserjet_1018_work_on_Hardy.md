---
title: "Does HP Laserjet 1018 work on Hardy?"
date: 2008-04-29
forum: Hardware
---

### Post by nubbe on 2008-04-29
Does HP Laserjet 1018 work on Hardy?

(I need a printer before I reinstall...)

Nubbe

---

### Post by subzero316 on 2008-04-29
Yes it does perfectly.

Try this link  [<<------Click Me-------->>]("http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018")

---

### Post by sub2007 on 2008-04-29
I have that exact printer and I can guarantee that (at least on my box) it works perfectly. Was ready to print as soon as Hardy was installed, no tweaking needed at all.

---

### Post by nubbe on 2008-05-01
Cool, thanks.

I'll take the plunge now.

---

### Post by Ludwig9 on 2008-05-02
I am a first-time user of Ubuntu (8.4), but my HP 1018 does not work with it. The computer recognizes the printer and says it is ready to print the printer test page, but that test page never prints, nor do any office files. The installation seems to me peculiar; I'm going to delete the HP1018 from another computer where it does work and then re-install it there, just to see what the process is; I will then try to duplicate that process on my other computer with Ubuntu. Any suggestions would be appreciate.

---

### Post by Ludwig9 on 2008-05-05
[FONT="Times New Roman"]I tried to install the driver following the instructions at [http://foo2zjs.rkkda.com](http://foo2zjs.rkkda.com) and got the following result. 

X@X-desktop:~$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)

--11:18:01--  [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)

           => `foo2zjs.tar.gz'

Resolving foo2zjs.rkkda.com... 74.208.41.246

Connecting to foo2zjs.rkkda.com|74.208.41.246|:80... connected.

HTTP request sent, awaiting response... 200 OK

Length: 1,550,126 (1.5M) [application/x-tar]



100%[=================================================================================================================>] 1,550,126    616.83K/s             



11:18:07 (614.99 KB/s) - `foo2zjs.tar.gz' saved [1550126/1550126]



X@X-desktop:~$ tar zxf foo2zjs.tar.gz

X@X-desktop:~$ cd foo2zjs

X@X-desktop:~/foo2zjs$ make

#

# Dependencies...

#

      ***

      *** Error: /usr/include/stdio.h is not installed!

      ***

      *** Install Software Development (gcc) package

      *** for Ubuntu: sudo apt-get install build-essential

      ***

make: *** [all-test] Error 1

X@X-desktop:~/foo2zjs$ 



I evidently need to install more software: the gcc package and sudo apt-get install. And what else?
Any advice from people here would be much appreciated. If I do not need to use the Terminal to get this printer working, please tell me. Thanks.[/FONT]

---

### Post by Ludwig9 on 2008-05-05
[FONT="Times New Roman"][/FONT] I have no idea why my previous post appears in the Greek alphabet. I will try again here. I have tried to install the foo2zjs driver for the HP 1018 by following the instructions at [http://foo2zjs.rkkda.com](http://foo2zjs.rkkda.com) but it tells me that I need more software: the gcc package and sudo.
Any advice from members here would be appreciated. Do I really need to use Terminal to install this driver?
And why did some of my previous post appear in the Greek alphabet? (as this one may also!)

---

### Post by nubbe on 2008-05-05
U need to install the package 

build-essential

Btw, my 1018 doesn't work either...

---

### Post by sub2007 on 2008-05-05
I'm not sure why it won't recognise it, I have had to compile the driver in the past though and so I'll try walking you through the install. We DO have to use Terminal unfortunately but don't be frightened of it, the installation is fairly straightforward but I can understand that it seems intimidating. Just copy and paste the commands exactly (remember to use CTRL, SHIFT and INSERT in Terminal to paste) and press ENTER after entering each command. Please make sure that you do do ALL the steps and in the right order and don't close the terminal between each step, you should be able to do all the steps in one terminal window.

Delete whatever package you have downloaded already first as we'll download it again to make sure you have the right one.

1. Open your terminal and enter the following:

```
sudo apt-get install build-essential
```

Enter your password and press ENTER again. Accept the dependencies by pressing "y" and then ENTER. Wait for the install to finish

2. In your terminal, enter the following:

```
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
``` 

3. When the file has downloaded, enter the following.

```
tar zxf foo2zjs.tar.gz
```

4. Paste the following command:

```
cd foo2zjs
```

5. Now comes time to make the driver. Paste the following:

```
make
```

**IMPORTANT: any errors at this stage then stop and post them back**

6. Assuming there were no errors (I don't anticipate any) then enter the following:

```
./getweb 1018
```

7. Enter the following command:

```
sudo make install
```

If you get asked then enter your password and press ENTER.

8. Enter the following command:

```
sudo make install-hotplug
```

You shouldn't be asked for your password but if you then enter it.

9. Unplug your printer and plug it back in again.

10. Now restart CUPS

```
sudo make cups
```

11. Now enter the following:

```
sudo system-config-printer
```

This will (finally) bring you back into a GUI interface. Delete any printer that's obviously HP 1018 then click to Add A New Printer. Select the model and then when asked which PPD file to use, don't use the default but select Foomatic foo2zjs 1018 (can't remember exactly what it says now but it should be easily recongisable as something like that). 

12. Close the CUPS manager (not the terminal). Just to make sure, do one final restart of CUPS in Terminal:

```
sudo make cups
```

Close the terminal, cross your fingers and hopefully the printer should now work!

---

### Post by Ludwig9 on 2008-05-05
> **Ludwig9 said:**
> [FONT="Times New Roman"][/FONT] I have no idea why my previous post appears in the Greek alphabet. 
Part of that post and parts of the other posts in this thread appeared to me in Greek letters, after I submitted the post although it (and the others) did not so appear to me before I clicked on Submit. I don't know why it did this; I am now using Windows, and it and the others appear to me in the English alphabet. I have no clue as to why.:confused:

---

### Post by game_plan on 2008-05-05
Have any of you tried just adding the printer via admin>printing.

I have the HP LJ 2600n which uses the same foo2hp driver and it comes pre installed with Hardy, it works perfect for me, colour and all.

---

### Post by nubbe on 2008-05-05
game_plan:  I've tried that, no go...

sub2007: I got to "make" and got this output in the end. Does it qualify as error messages?
slxdecode.1:172: a magic token is invalid within \X
slxdecode.1:172: a magic token is invalid within \X
slxdecode.1:172: a magic token is invalid within \X
foo2hiperc-wrapper.1:173: a magic token is invalid within \X
foo2hiperc-wrapper.1:173: a magic token is invalid within \X
foo2hiperc-wrapper.1:173: a magic token is invalid within \X
foo2hiperc-wrapper.1:173: a magic token is invalid within \X
foo2hiperc.1:173: a magic token is invalid within \X
foo2hiperc.1:173: a magic token is invalid within \X
foo2hiperc.1:173: a magic token is invalid within \X
foo2hiperc.1:173: a magic token is invalid within \X
hipercdecode.1:172: a magic token is invalid within \X
hipercdecode.1:172: a magic token is invalid within \X
hipercdecode.1:172: a magic token is invalid within \X
hipercdecode.1:172: a magic token is invalid within \X
foo2zjs-pstops.1:172: a magic token is invalid within \X
foo2zjs-pstops.1:172: a magic token is invalid within \X
foo2zjs-pstops.1:172: a magic token is invalid within \X
foo2zjs-pstops.1:172: a magic token is invalid within \X
arm2hpdl.1:172: a magic token is invalid within \X
arm2hpdl.1:172: a magic token is invalid within \X
arm2hpdl.1:172: a magic token is invalid within \X
arm2hpdl.1:172: a magic token is invalid within \X
usb_printerid.1:172: a magic token is invalid within \X
usb_printerid.1:172: a magic token is invalid within \X
usb_printerid.1:172: a magic token is invalid within \X
usb_printerid.1:172: a magic token is invalid within \X

That was the last. It was perhaps 3 times more before that.
Before that it looked ok.

---

### Post by sub2007 on 2008-05-05
I've never seen those errors before! It didn't say that anything failed to make so keep going and see if it works overall...

---

### Post by nubbe on 2008-05-05
Thanks a whole bunch sub2007 it worked like a charm. I rebooted and I could still print so I should be fine.
I think sudo gnome-cups-manager should be 
sudo system-config-printer
though.

Thanks again

---

### Post by Ludwig9 on 2008-05-05
Sub2007, thanks for your help! I got as far as: sudo gnome-cups-manager and then received the following:
# If you use CUPS, then restart the spooler:

#	make cups

#

# Now use your printer configuration GUI to create a new printer.

#

# On Redhat 7.2/7.3/8.0/9.0 and Fedora Core 1-5, run "printconf-gui".

# On Fedora Core 6 and Fedora 7/8, run "system-config-printer".

# On Mandrake, run "printerdrake"

# On Suse 9.x/10.x, run "yast"

# On Ubuntu 5.10/6.06/6.10/7.04, run "gnome-cups-manager"

# On Ubuntu 7.10, run "system-config-printer".

X@X-desktop:~/foo2zjs$ sudo make install-hotplug

#

# Hotplug Installation Dependencies...

#

# ... OK!

#

if [ -d /etc/udev/rules.d ]; then \

	    install -c -m 644 hplj10xx.rules /etc/udev/rules.d/11-hplj10xx.rules; \

	fi

[ -d /etc/hotplug/usb ] || install -d -m 755 /etc/hotplug/usb/

install -c -m 755 hplj1000 /etc/hotplug/usb/

ln -sf /etc/hotplug/usb/hplj1000 /etc/hotplug/usb/hplj1005

ln -sf /etc/hotplug/usb/hplj1000 /etc/hotplug/usb/hplj1018

ln -sf /etc/hotplug/usb/hplj1000 /etc/hotplug/usb/hplj1020

ln -sf /etc/hotplug/usb/hplj1000 /etc/hotplug/usb/hpljP1005

ln -sf /etc/hotplug/usb/hplj1000 /etc/hotplug/usb/hpljP1006

ln -sf /etc/hotplug/usb/hplj1000 /etc/hotplug/usb/hpljP1505

/etc/hotplug/usb/hplj1000 install-usermap

/etc/hotplug/usb/hplj1005 install-usermap

/etc/hotplug/usb/hplj1018 install-usermap

/etc/hotplug/usb/hplj1020 install-usermap

/etc/hotplug/usb/hpljP1005 install-usermap

/etc/hotplug/usb/hpljP1006 install-usermap

/etc/hotplug/usb/hpljP1505 install-usermap

X@X-desktop:~/foo2zjs$ sudo make cups

if [ -x /etc/init.d/cups ]; then \

	    /etc/init.d/cups restart; \

	elif [ -x /etc/rc.d/rc.cups ]; then \

	    /etc/rc.d/rc.cups restart; \

	elif [ -x /etc/init.d/cupsys ]; then \

	    /etc/init.d/cupsys restart; \

	elif [ -x /etc/init.d/cupsd ]; then \

	    /etc/init.d/cupsd restart; \

	elif [ -x /usr/local/etc/rc.d/cups.sh ]; then \

	    /usr/local/etc/rc.d/cups.sh restart; \

	elif [ -x /usr/local/etc/rc.d/cups.sh.sample ]; then \

	    cp /usr/local/etc/rc.d/cups.sh.sample /usr/local/etc/rc.d/cups.sh; \

	    /usr/local/etc/rc.d/cups.sh restart; \

	fi

 * Restarting Common Unix Printing System: cupsd                                                                                                      [ OK ] 

X@X-desktop:~/foo2zjs$ sudo gnome-cups-manager

sudo: gnome-cups-manager: command not found

X@X-desktop:~/foo2zjs$ 



I forgot to follow your command to: "Delete whatever package you have downloaded already first..." But I would not have known how to do this in any case. Also, at least on my system, I do not need to use CTRL, SHIFT, INSERT in Terminal to paste. I just right click and PASTE appears. Should there be a semi-colon after "sudo" in the command: "sudo gnome-cups-manager"? Thanks for your help; we're getting there. What are your further suggestions? Btw, much of this thread still appears to me in Greek letters, but not the commands which you have written.

---

### Post by Ludwig9 on 2008-05-05
Perhaps I should follow Nubbe's suggestion and write:
sudo system-config-printer

I will wait (at least a while) and follow your directions, Sub2007, before doing that.

---

### Post by Ludwig9 on 2008-05-05
sub2007 and nubbe, IT WORKS! I did what nubbe suggested and then followed the rest of sub2007's directions. Thanks. I still haven't figured out how to officially thank people here, but when I do you will receive it from me. Also I managed to correct my problem with Greek letters. Thanks again!

---

### Post by nubbe on 2008-05-05
Great that it worked for u too.

Good night  :)

---

### Post by sub2007 on 2008-05-05
No problem! I've had to exactly the same on both Feisty and Gutsy (and I think I had to do it a few times on Feisty, for some reason it kept losing my driver!) When I installed Hardy it recognised it, out of the box, didn't even have to add the printer - it was just there installed and waiting! So maybe I was just lucky, TBH it was just a nice bonus, I was set up ready to compile the driver anyway....

---

### Post by Ludwig9 on 2008-05-05
I have one further question: I had already downloaded the driver foo2zjs onto my desktop. Was it necessary in Step 2 of Terminal to give an internet address? or could I have said something like: 
wget -O foo2zjs.tar.gz desktop.foo2zjs.tar.gz

---

### Post by sub2007 on 2008-05-06
Yeah like I said, I thought you had downloaded it but I wanted to make sure that you had the right version. If you had it on your Desktop then you didn't have to do a wget, wget is basically a terminal download manager. Instead of doing the wget step then you would substitute that step with:

```
cd Desktop
``` (which basically just changes the directory to the Desktop).

As you already have the file then you can carry on from the next step.

---

### Post by PaulGrahamRaven on 2008-05-07
OK, so I'm trying to install an HP1018, literally out of the box today, on Gutsy (fully updated).

I've run through the instructions here about three times, and a similar set elsewhere three times, with no untoward error messages. Almost always the same result - the printer reported as installed and ready in the GUI, but nothing would print. I now have a different result, in that when I open the GUI at the end of the process, the system doesn't even see the printer as existing at all, so I can't select it and move on to driver choice in the "add new printer" dialogue.

Any advice? Is there some way I can revert my system to a clean no-printers-installed configuration and try again from scratch? If so, what should I remove and how? If not, what else should I try?

Your help would be greatly appreciated.

---

### Post by PaulGrahamRaven on 2008-05-07
OK, just tried removing and reinstalling anything to do with foomatic via Synaptic, uninstalled the foo2vjs driver, deleted the directory it installed to, and did it all again from scratch. System still can't see that there's a printer connected to the USB ports at all. I'm baffled ... I'm also hoping that multiple attempts haven't somehow borked the printer.

---

### Post by PaulGrahamRaven on 2008-05-07
Right, the complete removal/reboot/reinstall has me back to square one; the system now sees there is an HP 1018 connected, reports it as idle in the CUPS GUI and so on. But will it print? No sir, it will not. Jobs simply sit in the print queue and nothing happens ... which as far as I can tell is the problem that the lengthy installation procedures I've just gone through are supposed to cure!

Someone please point out whatever my obvious mistake has been?

---

### Post by sub2007 on 2008-05-07
It sounds like the printer is stopped but still accepting jobs. I often had the problem where the printer would randomly stop after you send a job to it (doesn't seem to have happened yet in Hardy). If you go into CUPS and restart it and it will print every job you sent to it.

To start the printer:

1. Go into the CUPS control panel. To get into it, open your favourite web browser and enter:

127.0.0.1:631/printers

2. Scroll down to where your printer is listed. There will be a number of buttons. One of which will either be a red button marked "Stop Printer" or a green one marked "Start Printer". If it is green then click it. When the authentication box comes up, enter your Ubuntu user name and password. That should start the printer and then jobs should start to print/be able to print.

You should be warned that if this IS the case then it will print TWO copies of the job that made the printer stop, so you should look at the jobs list and delete any obvious duplicates before restarting the printer.

---

### Post by PaulGrahamRaven on 2008-05-07
Thanks for that, sub, it's appreciated - I didn't know about the browser interface. Unfortunately that doesn't seem to have fixed it; the lights were all green when I got there. I cycled through 'em a few times to be sure, as well.

Don't know if it's relevant, but while I had the CUPS open I thought I'd try unplugging the USB cable then reinserting it ... didn't seem to register the disconnection, even after a few minutes.

Any more ideas?

---

### Post by sub2007 on 2008-05-07
Well about CUPS if they are configured right then they should look like this:

[img]http://ubuntuforums.org/attachment.php?attachmentid=69149&stc=1&d=1210188429[/img]

Sounds like you might have ANOTHER problem that I had with this printer a long time ago (I think when I was on Feisty!) 

Type in this command and see if anything comes up:

```
ls /usr/share/foo2jzs/firmware/
```

---

### Post by PaulGrahamRaven on 2008-05-07
```
No such file or directory
```

OK, so what's the fix? I thought I'd downloaded the firmware as part of the previous processes ... it's a jolly old learning curve, this command line business! :)

---

### Post by sub2007 on 2008-05-07
That's kind of what I was expecting. OK then let's try this. Do the steps in order, pressing ENTER after each one.

```
wget http://foo2zjs.rkkda.com/firmware/sihp1018.tar.gz
```
```
tar xvzf sihp1018.tar.gz
```
```
arm2hpdl sihp1018.img > sihp1018.dl
```
```
sudo cp ./sihp1018.dl /usr/share/foo2zjs/firmware/sihp1018.dl
```
```
sudo cat /usr/share/foo2zjs/firmware/sihp1018.dl > /dev/usb/lp0
```

What this does is sends the firmware to your printer. The first steps are downloading it, then converting to the format to one the printer can use, then putting it in the right place (the directory I asked you to check) and then finally sending it to the printer. Cross your fingers and hopefully it'll work!

---

### Post by PaulGrahamRaven on 2008-05-07
Ah-ha, I think we may have unearthed the problem, then; everything goes fine until:

```
x@y:~$ sudo cat /usr/share/foo2zjs/firmware/sihp1018.dl > /dev/usb/lp0
bash: /dev/usb/lp0: No such file or directory
```

So the printer isn't appearing at the URI where it's supposed to be ... how do I find out where it is? And (probably more importantly) why isn't it where it should be?

---

### Post by sub2007 on 2008-05-07
I had the same problem once, I mapped it to lp1. Let's just check which you have.

Open your Terminal and type:

```
ls /dev/usb/
```

And post back what the results of that are.

---

### Post by PaulGrahamRaven on 2008-05-07
Hah! This is weird:

```
No such file or directory
```

So I took a browse in my file system; there's a directory /dev/bus/usb/, and that has five subdirectories (001 - 005) in it, all showing as empty.

I take it I've just discovered why I had so much fun getting anything to work on this motherboard under w1nd0$e? Other USB stuff functions fine, though; mouse is USB, for a start, and my camera and PMP player cables, and a thumb drive ... what the hell is up with this daft box?

---

### Post by sub2007 on 2008-05-07
I have an lp0 in my /dev/ so maybe you have and that might help us to get it working.

Try running this:

```
ls /dev/ | grep "lp"
```

And post the output.

---

### Post by PaulGrahamRaven on 2008-05-07
Short but sweet:

```
lp0
```

---

### Post by sub2007 on 2008-05-08
Fantastic! In that case do the following:

```
sudo ln -s /dev/lp0/ /dev/usb/lp0/
```

That just makes a symbolic link (which is similar to a shortcut in Windows) and then that should make the hotplug work.

To finish off just run this step again:

```
sudo cat /usr/share/foo2zjs/firmware/sihp1018.dl > /dev/usb/lp0
```

---

### Post by PaulGrahamRaven on 2008-05-08
Not so fantastic ...
```

ln: target `/dev/usb/lp0/' is not a directory: No such file or directory
```
I had a look in the GUI browser, there's a file called lp0 that has an icon like a piece of paper with an X at the upper right corner ... does that explain it?

---

### Post by PaulGrahamRaven on 2008-05-09
Would it help if I create an empty /dev/usb/lp0/ directory? Or am I completely misunderstanding how symbolic links work?

---

### Post by sackbj on 2008-05-09
I had an HP Laserjet 1018 and it worked perfectly with any linux install I did (old Fedora, Ubuntu, and SUSE releases at least) - out of the box.  I can't speak to Hardy.

It does not, however, work on Vista.  It still has the "your product will be supported soon" tag on it on the HP website.

---

### Post by PaulGrahamRaven on 2008-05-09
Doesn't surprise me at all, sackbj.

That said, doesn't go far towards solving my problem here; evidently I have some sort of non-standard device configuration. Can anyone tell me how to get this printer to show up so I can send the firmware to it?

---

### Post by sub2007 on 2008-05-09
I'm sorry, I forgot you didn't have a /dev/usb/ directory. Yes you need to create a blank directory.

```
sudo mkdir /dev/usb
```

Then try to make the symbolic link again.

---

### Post by PaulGrahamRaven on 2008-05-09
Created the directory fine, but the symbolic link flops:

```
x@y:~$ sudo mkdir /dev/usb
[sudo] password for x:
x@y:~$ sudo ln -s /dev/lp0/ /dev/usb/lp0/
ln: target `/dev/usb/lp0/' is not a directory: No such file or directory
```

"So, maybe I should create an lp0 directory," I thought.

```
x@y:~$ sudo mkdir /dev/usb/lp0
x@y:~$ sudo ln -s /dev/lp0/ /dev/usb/lp0/
x@y:~$ sudo cat /usr/share/foo2zjs/firmware/sihp1018.dl > /dev/usb/lp0
bash: /dev/usb/lp0: Is a directory
```

I thought wrong! Any more ideas? Sorry for being such a damned n00b.

---

### Post by sub2007 on 2008-05-09
Don't worry that was my fault, I'm so sorry. I typed the symbolic link wrong! This one should work:

```
sudo ln -s /dev/lp0 /dev/usb/lp0
```

---

### Post by PaulGrahamRaven on 2008-05-10
No need to apologise, man - your patience is very much appreciated. But I'm afraid it's not over yet! File created, symbolic link created. But then:
```

x@y:~$ sudo cat /usr/share/foo2zjs/firmware/sihp1018.dl > /dev/usb/lp0
bash: /dev/usb/lp0: Permission denied
```

So I've pre-guessed your next question, gone to /dev/usb/ and done ls -l:

```
x@y:/dev/usb$ ls -l
total 0
lrwxrwxrwx 1 root root 8 2008-05-10 07:04 lp0 -> /dev/lp0
```

Because I'm not sure how to display what group has permissions to work on a file, I had a look in the GUI file browser; the 'lp' group has read-write permissions on /dev/usb/lp0 . The same applies to the 'original' lp0 (i.e. /dev/lp0 ).

Any ideas?

---

### Post by PaulGrahamRaven on 2008-05-11
Can anyone offer the final piece of the puzzle? I really need to be able to print out my invoices and receipts without going to the local web cafe ...

---

### Post by sub2007 on 2008-05-11
Sorry about the delay, I didn't forget about you but I've been trying to research this problem a bit more. 

Can you post the output of this:

```
ls -l /dev/ | grep lp0
```

---

### Post by PaulGrahamRaven on 2008-05-11
Here we go:
```

crw-rw---- 1 root   lp        6,   0 2008-05-11 11:05 lp0
```

---

### Post by sub2007 on 2008-05-11
OK what we'll try is to copy the file in /dev/ into /dev/usb/ so that we can play with it there. I don't want to break the one in /dev/ if we do something wrong (which I doubt we will but let's play safe).

So delete the symbolic link:

```
sudo unlink /dev/usb/hp0
```

Then to copy the file:

```
sudo cp /dev/hp0 /dev/usb/
```

Now we have a copy of that file in /dev/usb then we'll try altering the permissions on it. It needs to be 666.

```
sudo chmod 0666 /dev/usb/lp0
```

Then try the dreaded command again:

```
sudo cat /usr/share/foo2zjs/firmware/sihp1018.dl > /dev/usb/lp0
```

---

### Post by PaulGrahamRaven on 2008-05-11
Still not quite going as planned; got half way, but error messages:

```
x@y:~$ sudo unlink /dev/usb/hp0
[sudo] password for x:
unlink: cannot unlink `/dev/usb/hp0': No such file or directory
x@y:~$ sudo unlink /dev/usb/lp0
unlink: cannot unlink `/dev/usb/lp0': No such file or directory
x@y:~$ sudo unlink /dev/lp0
x@y:~$ sudo cp /dev/hp0 /dev/usb/
cp: target `/dev/usb/' is not a directory: No such file or directory
x@y:~$ sudo cp /dev/hp0 /dev/usb/hp0
cp: cannot stat `/dev/hp0': No such file or directory
x@y:~$ 
```

As you can see, tried some second guessing. Maybe there's just something utterly incompatible about the way this mobo deals with USB?

---

### Post by sub2007 on 2008-05-12
Ah I'm so sorry I typed the wrong thing! I feel so stupid! If it wasn't a hp printer it would be easier :D Try this:

```
sudo cp /dev/lp0 /dev/usb/lp0
```

Then carry on from the chmod step.

---

### Post by PaulGrahamRaven on 2008-05-12
Man, I'll bet you regret replying to this thread in the first place by now ... but that's a no-goer as well:
```

x@y:~$ sudo cp /dev/lp0 /dev/usb/lp0
[sudo] password for x:
cp: cannot create regular file `/dev/usb/lp0': No such file or directory
```

---

### Post by sub2007 on 2008-05-13
OK let's just do it the dangerous way. Normally it's not recommended for people to use GUI root file browsers but I'm fed up fighting.

```
gksu nautilus /dev/
```

**[color=red]REMEMBER: this is a root file browser and so you have the potential to destroy your whole system. It won't care if you delete even your entire filesystem. Please be careful what you delete or modify and close it as soon as you are finished[/color]**

Find the file **lp0** and copy it. Then in the same file browser (the root one) navigate to **/dev/usb/** and copy the file there. If there is no directory /dev/usb/ then create one. Close the file browser.

Then run the chmod step.

---

### Post by PaulGrahamRaven on 2008-05-13
Heh - I know the dangers of root-access GUI browsers. I've killed a few Wind0$e installs that way in my time. Anyway, no dead sysytem this time, but no luck either; pasting the file in the browser has no effect - the new directory stays empty. The following error message tuns up in the terminal:

```
** (nautilus:6762): WARNING **: No description found for mime type "x-special/device-char" (file is "lp0"), please tell the gnome-vfs mailing list.
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSx@y:~$
```

I had a look at the file properties for lp0; it registers as 0 bytes in size, if that makes any difference. I think I may just have to accept that either this printer and my machine are not destined to work together, or that there's some serious problem with my current Ubuntu installation.

---

### Post by sub2007 on 2008-05-13
Yeah it's not looking good, I'm really sorry but I've run out of things to try. For what it's worth that file is meant to be 0 bytes in size.

It's so unusual because this printer is meant to work, out of the box. If not compiling the driver should sort it. I honestly don't know what the problem is here. If I were you I would head over to either the OpenPrinting forums: [http://forums.openprinting.org/index.php?18](http://forums.openprinting.org/index.php?18) or even better the foo2zjs forums (who write the driver): [http://foo2zjs.rkkda.com/forum/](http://foo2zjs.rkkda.com/forum/) (although their forum looks quieter) for help. There you will be able to find experts who will be better able to help you than I can, they may even be developers of the driver over there.

Good luck, hope it works out. And if you do get it fixed let me know!

---

### Post by PaulGrahamRaven on 2008-05-13
Well, I've given you a 'thanks' anyway, because you've put loads of effort into it. Not your fault it hasn't worked out. I suspect maybe this is something that just won't get sorted out until it's running on a fresh install ... maybe the old printer made some changes to the settings that conflict, I dunno. Thanks again, though!

---

### Post by sub2007 on 2008-05-13
You're more than welcome, I really wish we'd have had a better outcome. I hope that it does work on a fresh install, for all the work we've put in here it will most probably just work out of the box!

---

### Post by IronArjen on 2008-06-18
I followed the procedure.

1 problem: first you need to install gnome-cups-manager

sudo apt-get install gnome-cups-manager

2 problem: I get error messages but it does work! In my administration two printers appear, the old one that was istalled automatically ad de no work, the new one that does work.

---

### Post by martinarg on 2008-09-19
Great sub2007, this worked twice in my different installations.

Thanks a million.

---

### Post by la cónica on 2008-10-19
> **sub2007 said:**
> I'm not sure why it won't recognise it, I have had to compile the driver in the past though and so I'll try walking you through the install. We DO have to use Terminal unfortunately but don't be frightened of it, the installation is fairly straightforward but I can understand that it seems intimidating. Just copy and paste the commands exactly (remember to use CTRL, SHIFT and INSERT in Terminal to paste) and press ENTER after entering each command. Please make sure that you do do ALL the steps and in the right order and don't close the terminal between each step, you should be able to do all the steps in one terminal window.

Delete whatever package you have downloaded already first as we'll download it again to make sure you have the right one.

1. Open your terminal and enter the following:

```
sudo apt-get install build-essential
```

Enter your password and press ENTER again. Accept the dependencies by pressing "y" and then ENTER. Wait for the install to finish

2. In your terminal, enter the following:

```
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
``` 

3. When the file has downloaded, enter the following.

```
tar zxf foo2zjs.tar.gz
```

4. Paste the following command:

```
cd foo2zjs
```

5. Now comes time to make the driver. Paste the following:

```
make
```

**IMPORTANT: any errors at this stage then stop and post them back**

6. Assuming there were no errors (I don't anticipate any) then enter the following:

```
./getweb 1018
```

7. Enter the following command:

```
sudo make install
```

If you get asked then enter your password and press ENTER.

8. Enter the following command:

```
sudo make install-hotplug
```

You shouldn't be asked for your password but if you then enter it.

9. Unplug your printer and plug it back in again.

10. Now restart CUPS

```
sudo make cups
```

11. Now enter the following:

```
sudo system-config-printer
```

This will (finally) bring you back into a GUI interface. Delete any printer that's obviously HP 1018 then click to Add A New Printer. Select the model and then when asked which PPD file to use, don't use the default but select Foomatic foo2zjs 1018 (can't remember exactly what it says now but it should be easily recongisable as something like that). 

12. Close the CUPS manager (not the terminal). Just to make sure, do one final restart of CUPS in Terminal:

```
sudo make cups
```

Close the terminal, cross your fingers and hopefully the printer should now work!

I can't print with HPLaserJet1018 since I reinstalled Hardy. I tried to follow your directions here, but on the 5th step, I got an error:

~$ make
make: *** No targets specified and no makefile found. Stop.

I also had some trouble when I first installed the printer to Edgy, but it could be solved thanks to a ubuntu forum. I hope some of you can help me. Thanks a lot!

---

### Post by sub2007 on 2008-10-19
You are in home, you're not in the correct folder. Type:

```
cd foo2zjs
```

If you extracted to your Desktop

```
cd Desktop/foo2zjs
```

Then try step 5 again.

---

### Post by la cónica on 2008-10-19
Thanks a lot for the patience. I guess I missed a line. Ooops.

Before reading your answer I read another thread


and [swarup's post's]("http://ubuntuforums.org/showthread.php?p=5993212#post5993212") directions solved the issue.

I followed the same steps you told me to in the first place, only difference was

$sudo make uninstall 

before step 5 $make

---

### Post by sub2007 on 2008-10-19
I don't know why you'd need a sudo make uninstall first (you'd only need that if you'd installed the package before and if you installed it through Synaptic then you should use that to remove it before compiling) but glad it's fixed. ;)

---

### Post by la cónica on 2008-10-21
I didn't install the package via Synaptic. At least, not consciously. I guess it was a just-in-case line. I rprobably missed the 

$cd foo2zjs

command, before the

$make

as you pointed out. I could do with a few cups of Ubuntu at the Beginners' threads. Thanks again for your patience :)

---

### Post by guga31bb on 2008-11-02
fyi, sub2007's method works for me with intrepid. thanks!

---

