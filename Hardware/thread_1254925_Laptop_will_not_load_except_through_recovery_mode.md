---
title: "Laptop will not load except through recovery mode"
date: 2009-08-31
forum: Hardware
---

### Post by lshafer on 2009-08-31
(Note sure if I've posted this in the right section, if not, I'm really sorry and can someone move it?)

Since April sometime I've had this problem with my Dell laptop not loading correctly.  If I just open it up and start it it'll try to load but then get stuck on this black screen right before the Ubuntu login page.  I've let it sit there for hours and that's all it does, sit.

But if I restart it and hit Esc while Grub is booting and run it through recovery mode it'll take a lot longer but it loads just fine.  Occasionally it does this thing where it force checks the file system but it never has issues.

I didn't deal with this sooner because I haven't had any problems once I started running it through recovery mode, the only problem I have that is really annoying is that it won't go into hibernation mode once in awhile and I'll get this weird rainbow effect across the top two inches of my screen.

Anyone have any ideas?

---

### Post by tgeer43 on 2009-08-31
The first thing I would do is this:

Boot into recovery mode and make a backup copy of /boot/grub/menu.lst.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```Edit the original menu.lst.
```
gksudo gedit /boot/grub/menu.lst
```Find the kernel line of the kernel that you are trying to boot. It will look something like this:
```
kernel  /boot/vmlinuz-2.6.28-15-generic root=UUID=25779404-f668-4f49-a548-65a771c24d18  ro quiet splash
```Remove the 'quiet' and 'splash' options from the line so it looks something like this:
```
kernel  /boot/vmlinuz-2.6.28-15-generic root=UUID=25779404-f668-4f49-a548-65a771c24d18  ro
```Save the file and reboot. You'll now be able to watch the boot process as it unfolds (albeit very quickly) and hopefully see which step of the startup is causing it to hang.

tgeer

---

### Post by lshafer on 2009-08-31
It's not allowing me to edit menu.lst.  It says, "Gtk-WARNING **: cannot open display:

---

### Post by tgeer43 on 2009-08-31
Then try:
```
sudo nano /boot/grub/menu.lst
```or
```
sudo vi /boot/grub/menu.lst
```tgeer

---

### Post by lshafer on 2009-08-31
Alright, well, that worked.  It looks as if it's basically the recovery mode only I didn't have to select it.  It still takes absolutely forever to boot up though and there are a lot of buffer I/O error on device sda5, logical block 4 (5, 6, 7, etc) warnings that I'm noticing now.  Is this normal?

---

### Post by tgeer43 on 2009-08-31
> It looks as if it's basically the recovery mode only I didn't have to select it.What do you mean by this? I don't understand.

Oh, and I/O errors are never 'normal'.

tgeer

---

### Post by lshafer on 2009-08-31
Oh.  ^^  lol

By recovery mode I mean when I select to start my laptop through recovery mode I get this screen that is basically numbers in brackets with text after it explaining what process it is going through occasionally followed by an [OK].  i.e.

[ 123.4556] Process here.                [OK]

It happens every time and it takes about eight to nine minutes to actually get through all of this and then start the computer.

This time, when I started the computer after editing the file you showed me it did the same exact thing only I didn't have to ask it to do it, it just did it on its own.

The I/O errors look like this:

[ 315.678] Buffer I/O error on device sda5, logical block 4
[ 315.679] Buffer I/O error on device sda5, logical block 5

and so on down the line about nine times.  I see this maybe five times during the recovery mode.

(By the way, thank you so very much for taking the time to help me with this.)

---

### Post by tgeer43 on 2009-09-01
You are seeing all of the boot process text scrolling by because of the changes you made to menu.lst - and that was the whole point of the exercise.

You stated that the system was getting stuck during the boot process right before the login screen. By editing menu.lst I gave you a way to monitor the boot process to see exactly where it is hanging.

Now you seem to be saying that the system just boots slowly. So which is it? Does it halt prematurely during the boot process or does it boot successfully (albeit slowly) to the desktop?

If it's making it to the desktop then it's probably the I/O errors causing the slow boot. If it's freezing during the boot process then it could be something else.

If it does freeze prematurely and fail to complete the boot process then write down the last few lines that were displayed and put them in your next message.

tgeer

---

### Post by lshafer on 2009-09-01
You're right.

Maybe it wasn't actually freezing, just staying on the black screen until it finally ran through the whole boot process and I just didn't wait long enough.  (Though I literally left it on all night once.)

It loads fine, very slowly, but fine and once it is loaded I don't have any issues with speed or file systems being corrupt or anything.

What causes I/O errors?

---

### Post by tgeer43 on 2009-09-01
I/O errors are caused by errors on the drive, physical or otherwise. They can be a sign of a failing drive but can also be from a number of other causes such as an improper shutdown, shock to the drive while writing, power failure, etc.

Now that you can monitor the boot process as it occurs you should be able to see when it is pausing. When this happens see what the last line printed was. If it's during the I/O errors then mystery solved. If it's during another process then post it here.

My guess is that the boot sector of the disk is borked and it's having to re-read it over and over again causing the pauses. If this is the case then the pauses should be occuring right after an I/O error message.

tgeer

---

