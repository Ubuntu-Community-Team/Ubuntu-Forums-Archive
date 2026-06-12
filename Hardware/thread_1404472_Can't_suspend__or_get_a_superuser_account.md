---
title: "Can't suspend  or get a superuser account"
date: 2010-02-11
forum: Hardware
---

### Post by Apetrunk on 2010-02-11
First of all I am using an HP TX2510US with XP Tablet Edition in addition to Ubuntu 9.10 (karmic).

As the title says, I can't suspend my computer, like when I would want to go between classes, and bring it back because it turns off the keyboard and mouse. By the time it's suspended, the keyboard and mouse are gone (which I can tell because moving the mouse and hitting buttons does nothing.) If I do suspend it, I have to hit the power button to bring it back or close the screen and open it again, but then I still don't have the keyboard and mouse and have to restart anyways.

Also, I am trying to run a .sh file and a .fdi file (that is supposed to work to turn the touch screen stuff on in Ubuntu) and it says I'm not a Superuser, but I can't find anywhere to let me make myself (the admin) a super user.

Any help is appreciated, even if it's just a link to another thread. I can read so if you tell me a thread has the information in it, that will be more than enough, but answering here would also be great. Thanks a bunch.

---

### Post by gdonwallace on 2010-02-11
The hibernate / suspend problem with Karmic has been an issue since Karmic was released.  Most people that try the suspend / hibernate find that they cannot get their laptops back on again and have to reboot.  As I don't use that on my laptop, I don't have any other helpful information other than searching through the forums and see what else might be out there.

To run anything as "super user" (admin) type **sudo ./<filename>.sh**  You will be asked for your password, enter that and press enter.  sudo allows you to run any program or command as super user / admin without having to actually be logged in as root.

Hope this helps.

---

### Post by Favux on 2010-02-11
Hi Apetrunk,

A link to another thread I can do.  This is [cenzorrll's thread]("http://ubuntuforums.org/showthread.php?t=1217745") where he solves it.

---

### Post by Apetrunk on 2010-02-11
It's a known problem? Ok thanks.

I tried that but it says the command isn't found.
I typed sudo ./setup-wacom.sh and it doesn't work. I'm probably just typing it wrong.

Thanks again.

---

### Post by sisco311 on 2010-02-11
> **Apetrunk said:**
> It's a known problem? Ok thanks.

I tried that but it says the command isn't found.
I typed sudo ./setup-wacom.sh and it doesn't work. I'm probably just typing it wrong.

Thanks again.

Type *sudo* and a space in the terminal, drag & drop the file in the terminal window to get the full path to it, then press Enter.

---

### Post by Apetrunk on 2010-02-11
Great. Thanks. Didn't know it was sudo '/<file address>'

---

