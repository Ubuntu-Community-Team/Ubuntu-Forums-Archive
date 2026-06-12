---
title: "problems with module raw1394"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by Keldek on 2007-01-02
I'm attempting to capture video via Kino and recieve the following error:

```
WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!
```

So I did some searching on these forums and found several solutions, unfortunately none that work for me.

A few things I do know however, there is no "/dev/raw1394" module whatsoever, and following the instruction of different posts to create one, automatically set permissions, and have it load at startup got me nowhere.

I know my firewire card is being recognized:

```
keldek@System-X:~$ lspci
[really long list of devices truncated]
04:07.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

but it does not mount or list at all in /dev

Camera make & model: Sony HDR-HC1
(all video recorded in DV format, not HDV)

So I'm at a loss at what to do ](*,) 

Any help is very much appreciated as video editing capabilities is essential for my switch from 'doze to linux. Thank you in advance

EDIT:

Additionally, I have this listed in my /etc/udev/rules.d/40-permissions.rules file:

```
# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",			GROUP="disk"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"
```

Not sure if this is important since there's no module at all for 'raw1394' in my /dev directory

---

### Post by presque on 2007-01-09
```
WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!
```

go to dev directory and change permission of raw1394 file ... will be 777 ... this is only with can i help you

---

### Post by zachthejones on 2007-12-02
hey, I'm having the same problem trying to capture DV camera footage via a firewire card. The irony is that in Feisty I had no problems, I just downloaded Kino and I could capture without difficulty from the beginning.

Now I'm getting the same error message. I went into Synaptic and installed all the raw1394 programs I could find, but still the same message.

Do I need to enable the read/write permissions for raw1394? If so, I need step-by-step instructions...i'm not so great at editing comand files and stuff.

---

### Post by daverich on 2007-12-03
I have the same problem.

There is no dev/raw1394 file to set permissions in.

Anyone?

Kind regards

Dave Rich

---

### Post by fustanella on 2007-12-16
Y'all are awesome. The chmod 777 on raw1394 did the trick. I didn't even have to restart kino.

---

### Post by oraldlight on 2007-12-24
chmod 777 also did the trick for me. So much for following the "how-to" on the kino forum...

thanks presque

---

### Post by eggdeng on 2007-12-24
> there is no "/dev/raw1394" module whatsoever
> There is no dev/raw1394 file to set permissions in.
This file is created only when the camera is *plugged in *and *turned on*.

---

### Post by Dougpol1 on 2008-01-15
I have the same problem but I don't understand where to put chmod 777  I went to dv 1394 file and it seems to be empty. Where do I and how do I find the device manager. and 1394 in it. I found the dev in home directory and !394 inside of it.  Sure would like some help here.

---

### Post by eggdeng on 2008-01-15
Simply type in a terminal ```
sudo chmod 777 /dev/raw1394
```
or ```
sudo chmod 777 /dev/dv1394
```
whatever the file is called.

---

### Post by Dougpol1 on 2008-01-16
OK, I get a reply:   chmod cannot access/dev/dv1394  no such file or directory  I copied and pasted command and tried both commands. Do I need to download this file and install in synaptic? I have the official Ubuntu book and tried to read about this raw 1394 but can't find any info on the subject I would like to better understand what I am doing here.    Thanks Doug

---

### Post by Dougpol1 on 2008-01-16
I brought in with synaptic  libraw 1394-b libraw 1394-dev and libraw 1394-doc do I need to install them in terminal with a command?   Thanks Doug

---

### Post by eggdeng on 2008-01-16
The file is sometimes called  /dev/raw1394-0 or similar. (You have !394 in a previous post but I sort of assumed it was a typo.) With your camera plugged in and turned on, run ```
ls /dev | grep 1394
``` to see if you can ascertain the correct name for the file. Then run the command as before substituting that name. 
(All I know about /dev/raw1394 is that it's a file that is created when you connect a firewire device. Kino needs to be able to access it to be able to use the device.) There is another thread about this issue at [http://ubuntuforums.org/showthread.php?t=454698]("http://ubuntuforums.org/showthread.php?t=454698")

---

### Post by Dougpol1 on 2008-01-16
Thank you, Thank you.  I have been struggleing download and opening tarballs and have had three successes. Amazing how complicated something is whenm you don't understand and  ipso presto, there it is,simple.       Thanks Doug

---

### Post by granny6989 on 2008-06-05
This is a combination of other posts that I have gotten together, since I had Kino working fine in Gutsy but lost it when changing to Hardy. Hopefully this will help you, Doug, as well as anyone else. 

Go to synaptic, and get:
[B]
libraw1394
libraw1394-dev
libdv4
dvgrab
libiec61883
libiec61883-dev
lidavc1394[/B]
   and of course **kino**

The tricky part now is giving yourself permission to use raw 1394, since it is normally advised against. I would think you'd be pretty safe unless you have other firewire devices that could let someone have random access to your machine.... Personally I find it a bit unlikely. Anyways, here's the next step:

open a terminal. change the directory:

**cd /etc/udev/rules.d**

now edit your permissions:

**sudo gedit 40-permissions.rules**

a few lines in is:

[B]KERNEL=="raw1394",			GROUP="disk"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"[/B]

change GROUP="disk" to GROUP="video", so that you have this:

[B]KERNEL=="raw1394",			GROUP="video"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"[/B]

_save_ and exit. Now type in terminal:
[B]
sudo modprobe dv1394
sudo modprobe video1394
sudo modprobe raw1394
sudo modprobe ohci1394[/B]

press enter after each command. They should just go in with no problems or messages. Next use your chmod command:
[B]
sudo chmod 777 /dev/raw1394[/B]

put your camera in vcr mode, and start kino. All should be functioning.
If not, maybe try logging out or restarting. My camera came up after entering the chmod command, without restart.

Good luck, I hope this will help a few people out there. The biggest discussion I've seen is the access to raw1394, which makes security issues, and most will argue that Kino should change their interface. I don't keep personal or secure info in my computer, so to me this really doesn't seem an issue. And I really don't know how easy it would be for someone to hack into your computer through firewire access. Anyways, enough about that....

By the way:
AMD64 running 32bit Hardy
Sony DCR-TRV30
Pinnacle PCI firewire card

S*
;-)

---

### Post by sattruckmark on 2008-06-05
Thanks for the instructions.  That even fixed a glitch I was having with Cinelerra.  Great info!

---

