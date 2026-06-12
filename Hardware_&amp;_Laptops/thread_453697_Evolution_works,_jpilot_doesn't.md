---
title: "Evolution works, jpilot doesn't"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by ziret on 2007-05-24
Hello,

At one time jpilot worked, as did Evolution in syncing my Palm. Now only Evolution works and I can't install new applications on the Palm. I don't know what has made the difference. Anyone know of a fix? When I look to install user in jpilot, it will not accept the correct name of my Palm.

Thank you,
Teri

---

### Post by lazyart on 2007-05-24
Does your connection method in Evolution match that in jpilot?  For instance, I use usb: for my T|X

What version of Ubuntu are you running?

---

### Post by ziret on 2007-05-24
I see now that I must have hit submit twice. Sorry. I will see if I can delete the other post.

I have feisty. I don't know how to change the setting in jpilot. In Evolution I assume it's usb because that's what I'm using and it works. Jpilot has a user name filed in but it's not the right one and I can't change it.

---

### Post by teripittman on 2007-05-24
I had to turn off the gnome-pilot applet and also turn off all sync within it to get jpilot to work. You should be able to uncheck everything within the sync configuration of Evolution. Give it a try before you do anything else.

---

### Post by ziret on 2007-05-24
Thanks I tried that, but it didn't work. Here is the message I get in Jpilot. It;s frustrating because it used to work

****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished
****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

Thanks

---

### Post by bapoumba on 2007-05-25
Hello, I deleted your duplicate thread.

Please check these bugs, not knowing your palm model:
[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=palm]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=palm")

Here is one that matches my own:
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/89723]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/89723")

If you find any related bug that needs infos, please comment in them. Thanks

---

### Post by ziret on 2007-05-25
I have a Tungsten T5. I don't think those bugs address my issue--they seem to be about mounting the Palm as a drive. That would be nice, but I can live without it. I just want to be able to add programs to my Palm.

---

### Post by teripittman on 2007-05-25
Did you push the hotsync button on your cradle BEFORE pushing the button in Jpilot? The USB device doesn't exist until you do that. I've been having to run that modprobe command to load the visor module before I can get it to work too. (Can't post the command just now but will try later today.)

---

### Post by ziret on 2007-05-25
Well, nothing works now. It acts as if it is synchronizing, but nothing changes, except my calendar did get wiped out. I have tried everything everyone said--one thing at a time.

---

### Post by ziret on 2007-05-28
It still doesn't work. Any more ideas?

---

### Post by Bingulim on 2007-05-28
I am on the same situation.

Jpilot used to work until Feisty.
Trying to find a solution too.

---

### Post by Bingulim on 2007-05-28
Ok, some progress.

I found out that there is a missing module that used to be up at Edgy, it is called "visor".
I think you need it if your palm is USP, like mine.
The command to get it going is:
```
$ sudo modprobe visor
```

Well, it is the first step.
I didn't sync it yet, but it is a little step closer.
At last, it stop complaining about missing /dev/pilot.

---

### Post by Bingulim on 2007-05-28
Well, after a nowhere crash, it is working.
Just with the modprobe command above.

Now I am looking how to set up to modprobe the module on the boot.
:popcorn:

---

### Post by Bingulim on 2007-06-01
Just to finalize the post, I found out how to set up a module to be started at boot.

Edit the following file (use your preferred editor):
```
$ sudo emacs /etc/modules 
```

And add the following line to the bottom of it:
```
visor
```

That's it!
Brilliant, doesn't it?

---

### Post by txHarleyMan on 2007-06-24
Worked like a champ for me!  Thank you.

Mike

---

