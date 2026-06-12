---
title: "Can't mount blackberry - Please Help"
date: 2010-06-07
forum: Hardware
---

### Post by Yehudah on 2010-06-07
I have installed Ubuntu 10.4 LTS onto my Dell 1536 AMD laptop. I've been struggling for two weeks with several issues. I'm not a newbie to Ubuntu, but I've become very frustrated with this version and I'm close to needing to go back to W7 (yeck).

I have surfed these and other forums for almost two weeks now and have used workarounds and supposed fixes that don't work. Here is one of my issues:

When I attach my blackberry curve 8530, it charges which is sweet, but I cannot mount the media card or the phones memory. I did lsusb and it sees the "RIM" device... but no matter what I try, it won't see the cards. I don't need to use Barry or sync or backup, I just want to be able to transfer files.

Can anyone assist me with this?

---

### Post by Dportner on 2010-07-06
i got the same problem when i updated to 10.04
found an answer??

---

### Post by SpyderBite on 2010-07-06
> **Yehudah said:**
> When I attach my blackberry curve 8530, it charges which is sweet, but I cannot mount the media card or the phones memory. I did lsusb and it sees the "RIM" device... but no matter what I try, it won't see the cards.

Exactly the same problem here since installing 10.04. In Karmic I never had a problem. No mass storage settings in the BB options have changed and as said before.. lsusb lists the blackberry. Have updated my usbids with sudo update-usbids but still a no-go.

---

### Post by SpyderBite on 2010-07-07
Fixed it with a complete driver update...

sudo apt-get update
sudo apt-get upgrade

Done.. recognized my Tour half way through the upgrade process. Now, to get it to work in Virtual Machine next! :)

Update: That only worked on my Dell Latitude X1 notebook. On my newer XPS 420 desktop no mass storage devices are recognised when plugged in. I've tried every solution on these forums and via google search. Even tried different USB cables and a different device of the same model. Still stuck.

---

### Post by SpyderBite on 2010-07-24
I got it working  but I have to boot in to VirtualBox, plug in my Blackberry, shutdown  VirtualBox to get it to recognize it each time. Pita.. but it'll do in a  crunch until a solution is coded in to an update later.

---

### Post by csuarezmtz on 2010-07-28
Please help!!!! I downloaded all the barry packages from synaptic, the run barrybackup, but the minute i plug in my bb curve it keeps booting, it shuts down, then starts again and keeps doing that over and over again. I'm not very familiar with ubuntu or any linux distro. I've been using ubuntu 10.4 for a month and have not been able to solve this.

Please help!!

---

### Post by Dportner on 2010-08-05
> **SpyderBite said:**
> I got it working  but I have to boot in to VirtualBox, plug in my Blackberry, shutdown  VirtualBox to get it to recognize it each time. Pita.. but it'll do in a  crunch until a solution is coded in to an update later.

this is EXACTLY what i have to do :S

ever since upgrade to 10.04... no BB tour support :(

any solutions??

---

### Post by kmrs75 on 2010-08-11
i got the BB to mount in ubuntu 

what i did was this 

sudo apt-get update
sudo apt-get upgrade


then i added opensync-plugin-barry-dbg

and then i pluged in BB and opened as a storage device 

now i need to get it to sync

---

### Post by Dportner on 2010-08-15
> **kmrs75 said:**
> i got the BB to mount in ubuntu 

what i did was this 

sudo apt-get update
sudo apt-get upgrade


then i added opensync-plugin-barry-dbg

and then i pluged in BB and opened as a storage device 

now i need to get it to sync

iv done all of this... still wont mount :(

---

### Post by stuart.reinke on 2010-08-27
Had the same trouble with my 8530.
What fixed it for me is this:
Under the options menu on the blackberry select memory
Turn off media transfer protocol
Turn on auto mass storage connect 
After I did these two changes the phone is recognized as a media player. Tell ubuntu to open with nautilus and all is good. 
Hope this works for you guys too.

---

### Post by dca on 2010-09-22
The problem stems from if you've installed the 'barry' and 'bcharge' applications.  With 'bacharge', a /etc/udev/rules.d/10-blackberry file is created that sets BB to charge @ 500mA versus mounting the media you have installed...  If you comment the lines out in 10-black***** it should mount, however, you may lose the ability to charge unit in faster time versus trickle charge @ 100mA...

---

### Post by hfw on 2010-10-01
dca,

you are awesome.

I have been fighting with this for ages.  When my dell m4400 was in the dock, it would not mount.  When it was out of the dock, it mounted the blackberry fine.  It was driving me nuts.

This fixed it.

Thanks,
hal

---

### Post by JeromeMorrow on 2011-02-02
> **dca said:**
> The problem stems from if you've installed the 'barry' and 'bcharge' applications.  With 'bacharge', a /etc/udev/rules.d/10-blackberry file is created that sets BB to charge @ 500mA versus mounting the media you have installed...  If you comment the lines out in 10-black***** it should mount, however, you may lose the ability to charge unit in faster time versus trickle charge @ 100mA...

Thanks, I manually erased this file in ubuntu and active massive storage in the blackberry and worked!!.

---

### Post by RecceDG on 2011-04-04
Same problem for me, BB 9700 - same solution. Comment out all lines in the 10-blackberry file and it auto-mounted.

Thanks much!

DG

---

### Post by Tanath on 2011-08-08
dca is correct. With barry installed it charges instead of mounting. You do not need to comment out the feature though. Barry installs the 'bfuse' command which can be used to mount the BB to the specified location:
  $ mkdir ~/bb && bfuse -o default_permissions ~/bb

---

### Post by utubuser on 2012-07-20
Blackberry button to the left of the central black touch box, then options, then memory, then Auto Enable Mass Storage Mode When Connected ---switch option to "Yes."

We had been on a trip and my mother had taken some photos and videos with her blackberry so when mine connected to ubuntu pc and hers wasn't was able to read a previous post that led to the memory option then compare the two blackberries to find the issue, regards, Thomas Metzentin

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

