---
title: "My system doesn't recognize my IEEE 1394 (firewire) adapter."
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by minimidgy on 2005-06-07
I'm trying to edit a video using kino, so I hooked an extension that has IEEE 1394 ports.  I have it hooked up to the camera and everything, all I need to do is to capture it in kino.  I went into preferences --> capture and this is what it says:

**The IEEE 1394 Subsystem is not responding.** 

The raw1394 module must be loaded, and you must have read and write access to /dev/raw1394.

I'm kinda new to linux, and so far I love it.  I'm not really sure how to configure this, so any help is appreciated.

---

### Post by mtron on 2005-06-07
is the device recognized by ubuntu? (not kino)

before pluggin' in the device, fire up a terminal and type "dmesg", then connect the firewire device and run again "dmesg".

is the device recognized? or post the new lines that appeard since the device was pluged in.

---

### Post by wylfing on 2005-06-07
To find out if raw1394 is loaded, issue the following command in a terminal (the password it asks you for is your regular login password):

```
sudo lsmod | grep 1394
``` 

To find out what the permissions of /dev/raw1394 are, issue the following command in a terminal:

```
ls -l /dev/raw1394
``` 

Paste the results of both commands here for our inspection.

---

### Post by minimidgy on 2005-06-07
[QUOTE=wylfing]To find out if raw1394 is loaded, issue the following command in a terminal (the password it asks you for is your regular login password):

```
sudo lsmod | grep 1394
``` 

To find out what the permissions of /dev/raw1394 are, issue the following command in a terminal:

```
ls -l /dev/raw1394
``` 

Paste the results of both commands here for our inspection.[/QUOTE]
```
*****@ubuntu:~$ sudo lsmod | grep 1394
Password:
*****@ubuntu:~$ ls -l /dev/raw1394
crw-------  1 root video 171, 0 2005-06-07 15:46 /dev/raw1394
*****@ubuntu:~$
```

---

### Post by mtron on 2005-06-08
it semms that the modules are not loaded. try loading them manually

sudo rmmod ohci1394
sudo rmmod sbp2
sudo modprobe ohci1394
sudo modprobe sbp2

and again
sudo lsmod | grep 1394

now it should display 

```
mtron@box:~$ sudo lsmod | grep 1394
Password:
ohci1394               31876  0
ieee1394              100408  2 ohci1394,sbp2
```

The permissions are ok

---

### Post by pimpaulogy on 2007-04-05
Has anybody found a resolution to this?

If so, please post.

---

### Post by UbiOneCanubi on 2008-05-05
Hi Pimpaulogy and Minimidgy,

I had the same problem when I downloaded Kino via the Synaptic Package Manager. Starting up the programme and checking Preferences > IEEE 1394 I was being told:
> **The IEEE 1394 Subsystem is not responding.**
The raw1394 module must be loaded, and you must have read and write access to /dev/raw1394.

So I started trawling the net for a solution. First of all make sure that you add the libraw1394-8 package (I have also installed the libraw1394-dev package but I don't think it's a necessity).

Once completed open up a terminal to find out whether or not you have read and write access to /dev/raw1394. To do that run [COLOR="Blue"]ls -l /dev/raw1394[/COLOR].

The output from my system looked like this before I fixed it:
```
sam@UbiOneCanubi:~$ ls -l /dev/raw1394
crw-rw---- 1 root disk 171, 0 2008-05-05 15:15 /dev/raw1394
sam@UbiOneCanubi:~$ tail -f /var/log/messages
May  5 13:05:53 UbiOneCanubi -- MARK --
May  5 13:20:09 UbiOneCanubi syslogd 1.5.0#1ubuntu1: restart.
May  5 13:45:53 UbiOneCanubi -- MARK --
May  5 14:05:53 UbiOneCanubi -- MARK --
May  5 14:25:53 UbiOneCanubi -- MARK --
May  5 14:45:53 UbiOneCanubi -- MARK --
May  5 15:05:53 UbiOneCanubi -- MARK --
May  5 15:15:45 UbiOneCanubi kernel: [ 9041.083313] ieee1394: raw1394: /dev/raw1394 device initialized
May  5 15:15:45 UbiOneCanubi kernel: [ 9041.100646] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.
May  5 15:25:53 UbiOneCanubi -- MARK --
May  5 15:45:53 UbiOneCanubi -- MARK --
```

The line you need to pay attention to is second from the top. It determines what kind of access you have to /dev/raw1394.

I noted on Minimidgy's earlier post that her code was in fact wrong:
```
*****@ubuntu:~$ ls -l /dev/raw1394
crw-------  1 root video 171, 0 2005-06-07 15:46 /dev/raw1394
*****@ubuntu:~$
```

The output should read:
```
sam@UbiOneCanubi:~$ ls -l /dev/raw1394
crw-rw-rw- 1 root disk 171, 0 2008-05-05 15:37 /dev/raw1394
```

Note that the output reads crw-rw-rw-. That seems to be the key, as I now am able to import footage from my dv cam into Kino - it determines the read/write access of /dev/raw1394 for all users. To correct this problem is as easy as inputting one line of code into your terminal:

```
sudo chmod a+rw /dev/raw1394 
```

This should make the appropriate changes. To check, simply run [COLOR="Blue"]ls -l /dev/raw1394[/COLOR] again.

My thanks go to Forrest whose blog "Adventures in Switching to Linux" ([http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html](http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html)) provided me the answer in the first place.

Hope this helps, I'm very new to Linux myself, hopefully my post makes sense.

Ubi

---

### Post by Corvair on 2008-06-11
I first was able to download from my Sony DCR-TR7000. My files were going to root as .dv files and I did not have permission and could not access my files.
I configured so my files were saved outside of root so I would have permission. Now my files are saved as .kino files instead of .dv files and I can only open them with kino. Why did it go from .dv to .kino? 

here is what I get from terminal.

raw1394                31624  0 
dv1394                 23400  0 
ohci1394               36532  1 dv1394
ieee1394              106968  4 sbp2,raw1394,dv1394,ohci1394
claude@claude-desktop:~$ sudo chmod a+rw /dev/raw1394
claude@claude-desktop:~$ ls -l /dev/raw1394
crw-rw-rw- 1 root disk 171, 0 2008-06-11 11:23 /dev/raw1394
claude@claude-desktop:~$ 


If you want more details let me know

---

