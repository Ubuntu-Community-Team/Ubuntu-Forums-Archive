---
title: "Logitech Quickcam Messenger Plus Driver?"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by Valburgh on 2009-02-24
Hi everyone, I'm new to Ubuntu and installed the 8.10 version a few days ago.
Yet I will have to get things to actually work before I could use the OS for a longer period of time.

I tried out Microsoft Windows Vista Ultimate before and couldn't get the needed drivers for The web cam.
Why buy a new Web cam only because the OS don't like it?
Vista was unstable and couldn't even accept my hardware.
So I just wanna finish up with Microsoft for good.

Now I got the same Problem with Ubuntu 8.10?
(Is Windows XP the only OS that actually does it's job?)

The web cam is a Logitech Quickcam Messenger Plus with the ID 046d:08f6 on the "lsusb" Terminal command.

Ubuntu doesn't seem to notice it. But the USB does.

I successfully installed the qc-usb-messenger-1.8 package.
But no resonance.

I'm already thinking about creating a own driver. The only problem is that I can't program any.

I'm really looking forward to make Ubuntu to my permanent OS. But I still got a lot of troubles to go through.

So what should I do about the Cam?

---

### Post by cariboo on 2009-02-24
THe driver for you webcam is more than likely loaded by default. TO check open a Applications-->Accessories-->Terminal and type:

```
lsmod | grep spca
```

the result should look something like this:

```
lsmod | grep spca
**gspca_zc3xx**            59392  0 
gspca_main             34560  1 gspca_zc3xx
compat_ioctl32         18304  2 saa7134,gspca_main
videodev               45184  4 tuner,saa7134,gspca_main,compat_ioctl32
```

I've bolded the driver in the output, if you have the above driver installed, your webcam should work. to make sure, use synaptic package manager to install xawtv. Once xawtv tv is installed in a terminal type:

```
xawtv -c /dev/video0
```

You should see your own smiling face looking back at you :)

Jim

---

### Post by Valburgh on 2009-02-25
First of all, thank's for your reply.

But, well, I opend the Terminal and enterd your first Code.


```
zorn@Soprano:~$ lsmod | grep spca
zorn@Soprano:~$
```

Hmm. There was not much of a reaktion from the Ubuntu 8.10 Terminal.
Did I miss something?

This is embarracing for me.

I googled arownd and saw that others did that too.
But my terminal dosn't reakt.
Users error probably.

Ps. I checked, I got xsawtv insalled.

---

### Post by Valburgh on 2009-02-27
No, this doesn't work at all.
This command doesn't react a bit.

The terminal doesn't even tell if this command exists or not.

No can do, and no reaction to the command: "lsmod | grep spca".

Anyone had the Idea yet to create a Linux Software that people could use to install the original windows based drivers into?
Something like a virtual adapter like WINE?

This would improve the whole Ubuntu compatibly story a lot.

Imagine, just download the windows drivers, install it to this (virtual driver adapter) Software and use.

Any professionals who could architect this?
I can't.

---

### Post by Valburgh on 2009-03-30
Ok, I lost my Internetconnection for Weeks. Now I have to get started again with the same old story.
How to install this Webcam on Ubuntu 8.10.
Or how to insall it on Virtualbox (XP).
Or how to install it at all.

My friends keep asking me when I'd go online again.
"No can do on Yahoo Messenger, Skype, MSN, or ICQ."
Their question:
"Why did you install Ubuntu anyway? There arrn't any drivers for it."
My answer:
"I'll see what I can do."

But well I can't do anything without no help.
And I'll have to give it a try at least for a month.
But then I am forced to return to XP to actually make use of my computer.
And I will just have to wait till I'll turn 60 for a better OS than XP to come.

Or I will have to study softwareprogramming and somday create a better OS myself.

I already got a nice name for it: "MISANTHROP".

Frustrated...

---

