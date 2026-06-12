---
title: "Is there a gfxboot guide for dummies/new users? (Hardy Heron)"
date: 2008-08-27
forum: General Help
---

### Post by debray6379 on 2008-08-27
Hi I am a newbie to ubuntu and still finding my feet on how to do things the right way...
I seen GFXBOOT in synaptic and wondered what it was so I search around and found that it made bootloader look better I thought cool!! so I looked for an easy guide to help me use it nothing (the only one I found was a good guide from [PingunZ]("http://ubuntuforums.org/member.php?u=37394")  [http://ubuntuforums.org/showthread.php?p=1212505#post1212505](http://ubuntuforums.org/showthread.php?p=1212505#post1212505))
But I got a bit miffed as what exactly to do the guide is good but for a noob I did not quite get some things to do???
like when it says to edit the menu.lst >>> What do I edit, what do I put in and where???
I mean no offence to anyone I think everyone that tries to help others need great thanks from all, as they have spent thier time to make these guide for the benefit of others!!
but could anyone PLEASE PLEASE let me know where to find an easy step by step guide to use gfxboot for Ubuntu Hardy Heron (for dummies like me)
I hope someone will answer me soon and thankyou for your time:)

---

### Post by lyni on 2008-08-27
I searched and found this site which may be of help
[www.joejoe.org/forum/index.php?showtopic=13873](www.joejoe.org/forum/index.php?showtopic=13873)
it seems to explain how to get to menu.1st
hope it helps

---

### Post by debray6379 on 2008-08-27
> **lyni said:**
> I searched and found this site which may be of help
[www.joejoe.org/forum/index.php?showtopic=13873]("http://www.joejoe.org/forum/index.php?showtopic=13873")
it seems to explain how to get to menu.1st
hope it helps

Thanks Ill check it out now =D>

---

### Post by Nepherte on 2008-08-27
I don't have any reason to use gfxboot. I guess some people like it more because they find it better looking. But I wonder who needs all these graphics on startup.

---

### Post by debray6379 on 2008-08-27
:confused: nope didn't work for me:confused::confused:
where it says...  Type 
CODE
sudo grub
Then
CODE
find /boot/grub/stage1
You will get a output like (hd0,4) or something different depending upon you Hard Disk Partition
I get....:~$ sudo grub
sudo: grub: command not found
~$ find /boot/grub/stage1
/boot/grub/stage1

thanks for your help and support!!!!

would it help if I did not remove grub at start???

---

### Post by debray6379 on 2008-08-27
> **Nepherte said:**
> I don't have any reason to use gfxboot. I guess some people like it more because they find it better looking. But I wonder who needs all these graphics on startup.
I guess it just something else to customize maybe?? I can see that it would not be everyones cup of tea... I know myself I thought I had installed ubuntu wrong the first time I saw it lol. and I personally think even though you only see the bootloader for a short time I'd like it to look nicer {but that is just me other people may have a different view}

EDIT
THIS IS MY TERMINAL READOUT>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

:~$ sudo su root
:/home/ray# nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6303): WARNING **: Unable to add monitor: Operation not supported
seahorse nautilus module shutdown
# sudo gedit /boot/grub/menu.lst
:/home/ray# nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6316): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

seahorse nautilus module shutdown

--- Hash table keys for warning below:
--> file:///

(nautilus:6316): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:6316): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
# sudo grub
sudo: grub: command not found

---

### Post by RSingh on 2008-09-22
bump

---

### Post by bigbrovar on 2008-09-22
u can try this guide it was what i used and it seems easy enough 
[http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/](http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/)

---

