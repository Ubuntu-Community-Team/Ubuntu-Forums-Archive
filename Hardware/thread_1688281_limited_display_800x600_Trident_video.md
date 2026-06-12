---
title: "limited display 800x600 Trident video"
date: 2011-02-15
forum: Hardware
---

### Post by krustybaguette on 2011-02-15
I started new thread but have same problem, different hardware. 

Re: How do i install grapic driver and get bigger than 800x600 resulution?

I am running into the same video problem with Ubuntu 9.04 on Toshiba Portege 7140CT. 500 Mhz Pentium III with max RAM of 320. I have located a driver for the machine but cannot figure out what to do with it. Based on an earlier entry in this thread my video is:

kenny@Portege7140CT:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: Trident Microsystems Cyber 9540 (rev 52)

I also have pages from the Portege's online manual which give further detail about the video hardware. I can probably locate the file again and paste that information into a subsequent posting.

The driver I found is in BladeXF86_SVGA.gz Filename is "XF86_SVGA"
"Properties" shows this to be an "executable" 
tar -xzvf (filename) replies...'does not appear to be a tar archive but opening it in GUI finds the above file.

I searched file system for an xorg.conf file and only result is a compressed file/folder "xorg.conf.5.gz" which contains a read only file "xorg.conf.5" As I understand it there should be an "xorg.conf" file at /etc/xorg.conf.

(edit this out)Is it possible that the above named file "SF86_SVGA" is merely a text file that needs to be cut and pasted into a new file and named /etc/xorg.conf? (END)

When I open System/Preference/Display my options are limited to 800x600. I assume this is based on some generic driver that gets you up and running. Yesterday's experimenting ended up crashing as rebooting sent me into a flashing screen that showed "login:" but did not respond to keyboard entries.

---

### Post by grahammechanical on 2011-02-15
Can the graphic card run at resolutions greater than 800x600? According to the Toshiba web site, yes it can. > 1,024 x 768 x 16.7 million colours

So, it must be possible. Did you try System>Administration>Drivers or Additional Drivers (as seen in 10.10)? This is how I install a video driver for my machine.

Regards.

---

### Post by krustybaguette on 2011-02-15
> **grahammechanical said:**
> Can the graphic card run at resolutions greater than 800x600? According to the Toshiba web site, yes it can. 

So, it must be possible. Did you try System>Administration>Drivers or Additional Drivers (as seen in 10.10)? This is how I install a video driver for my machine.

Regards.

No proprietary drivers show up in System/Administration>Hardware Drivers
Help says it may be necessary to download and install a driver. I've done the download but "Help" doesn't say how to install. I'd guess there might be a terminal command, or a specific directory to which to copy the driver but so far I'm stuck.
BTW, there is NO xorg.conf file in my filesystem. Thanks for above suggestion even though it didn't help...yet.

---

### Post by krustybaguette on 2011-02-15
Got the video problem licked. No driver needed. Just xorg.conf placed in /etc/X11. Found another user's Trident file, copied it into a blank text file, saved as xorg.conf and copied it in terminal using sudo cp <path to filename> /etc/X11. Upon rebooting I didn't even have to use System>Preferences>Display. Full Screen showed up during the boot process. ):P

Now I can start on getting my wireless adapter working.

---

### Post by bweewb on 2011-02-28
Would you please post the working xorg.conf file?  This would be much appreciated.

---

### Post by djrakun on 2011-03-03
+1 for the working xorg.conf. dont hold out!

---

### Post by dr_harika on 2011-03-18
Hi All,

I went around in circles finding a solution to this problem. Why would you NOT add the file after solving the issue!!!!!

Attached is a xorg.conf file (that has been renamed to xorg.doc so it can be uploaded to this forum) that actually works!!!

I have a Toshiba Satellite Pro 6000 with a 16mb Trident graphics adapter, and it worked for me running Ubuntu 10.10.


Instructions:
1 - Download xorg.doc from this post to a directory you can locate later.
2 - Rename it to xorg.conf
3 - Open Terminal and type: "sudo cp <path to filename> /etc/X11"
4 - Reboot
5 - Open System --> preferences --> monitor.. then select the highest resolution! :)
 

For the newbies like me(because this is my second day ever with Linux) the "sudo cp" command i think just copies the file to the /etc/X11 directory (which you otherwise cant copy to). 

Hope this helps people. 

dr_harika.

---

### Post by bluesmudge on 2011-04-17
Fantastic fix . .  great bit of random timing too as i've just been given an old Toshi SP6000 to play on!

It appears to be working fine with the new xorg.conf  -  a few video clitches but what do you expect for a 12 year only computer with 16 mb graphics!

---

