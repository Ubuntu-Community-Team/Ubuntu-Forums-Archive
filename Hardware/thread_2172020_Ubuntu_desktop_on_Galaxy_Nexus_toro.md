---
title: "Ubuntu desktop on Galaxy Nexus toro"
date: 2013-09-02
forum: Hardware
---

### Post by Samuel_A._Johns on 2013-09-02
Hi there, I have a little bit of a fun project I am working on, was wondering if anyone could help me out with it a little. Ubuntu touch looks pretty awesome, so I bought a secondhand Galaxy Nexus only to discover that you cant get Touch for it because it is the Verizon version (aka Toro), so I changed my end  goal a little. I want to try to run a dual boot with android and the desktop/netbook version  of ubuntu 12.04 on my phone and use it like I would a tablet (not even  sure if this is possible, if it isn't feel free to yell at me and call  me a noob, I just thought it would be cool) it seemed like a fun little  project until ubuntu touch is supported for the nexus toro. I am fully aware it would no longer connect to the mobile network, that's fine since it is not my main cellphone. I would want wifi to work, if that isnt possible please let me know as well. Anyway, I started with attempting to root and followed a thread on XDA dev's website (Link can be found [here]("http://forum.xda-developers.com/showthread.php?t=1506536")). Had a couple little hiccups trying to get the su.zip file to show up in clockworkmod, after reading another forum I did:[INDENT]   adb push su.zip /sdcard/
 [/INDENT]
and su.zip showed up in CWM, I was able to install it from CWM just  fine, did a reboot and everything was all good, or so I thought, it did say it had installed correctly. Anyway, I  went to the linux installer STD app and it said I didnt have root  access, i checked in the superuser app, the superSU app and a terminal on  the phone and confirmed I still do not have root access despite  following the directions step by step that seemed to work for others. Am I forgetting to do anything? Is  there a step that post leaves out? I would be happy to post any logs necessary, I use ubuntu regularly but mostly as an every day operating system and dont usually go 'under the hood' unless I am having a serious issue so if you do need anything, please keep that in mind. 

  
Thank you to anyone willing to take the time to help me out with this, I know it is sort of walking the fringe line between ubuntu and ubuntu touch which few people seem to want to cross.

---

### Post by jacksenechal on 2013-09-11
FYI I've just successfully put Ubuntu Touch onto my toro device. I followed the instructions on the [official install page]("https://wiki.ubuntu.com/Touch/Install"), with a small hack to one of the files to make it think the toro is a maguro.

Once you've added the "phablet-team/tools" PPA and installed phablet-tools, android-tools-adb and android-tools-fastboot, edit [FONT=Courier New]/usr/share/pyshared/phabletutils/environment.py[/FONT] and insert three lines below the line that says [FONT=Courier New]log.info('Device detected as %s' % device)[/FONT] (currently line 46)

```

    if device == 'toro':
        device = 'maguro'
        log.info('setting device to maguro')

```

Then you can run [FONT=Courier New]phablet-flash cdimage-touch -b[/FONT] and it will load on all of the maguro files. My device was already rooted, so that's all I had to do.

My main goal is to have a desktop version of Ubuntu on my Galaxy Nexus though, and at the moment it doesn't seem like this gets me anywhere toward that. It's worth a few minutes of playing around with Ubuntu Touch to see what it's like (I think it'll be really nice once it's ready for prime time), but otherwise it's pretty useless. 

I'll keep looking to see if there's a way to just get Ubuntu Desktop running on it, with bluetooth, HDMI and wifi so I can connect up a keyboard, mouse and monitor, get on the net, etc. I think the Galaxy Nexus is plenty powerful enough to be a laptop replacement... just need to figure out how to get the right software on it!

---

### Post by rvolkmar on 2013-10-11
I tried this, seemed to install just fine, but will only boot to GOOGLE screen, been trying to fix/recover with no luck, any ideas?

---

