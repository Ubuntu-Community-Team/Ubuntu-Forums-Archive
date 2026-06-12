---
title: "Quick cam under 7.10 won't work?"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by irv on 2007-10-27
After upgrading to 7.10 my webcam quit working. I have a Logitech cam and when I do a lsusb it shows "Bus 004 Device 005: ID 046d:08d7 Logitech, Inc." so it is showing it installed but when I run Camorama web cam viewer I get and error “Could not connect to video device (/dev/video0) Please check connection.
I am not sure what changed after doing the update? If I look in /dev the file video0 is there.
Any body have any ideas what to try.
Irv

---

### Post by iAtari on 2007-10-27
Hmm.. interesting. You were running 7.04 before?

My Logitech Quick Cam is recoginized as yours is, but when i'm networked on the internet the router blocks the webcam from showing.

Perhaps trying the webcam without internet connected to the computer. 

iAtari

---

### Post by swudee on 2007-10-27
I found that camera worked with Kopete instant messenger, though not the microphone.

---

### Post by irv on 2007-10-27
> **iAtari said:**
> Hmm.. interesting. You were running 7.04 before?

My Logitech Quick Cam is recoginized as yours is, but when i'm networked on the internet the router blocks the webcam from showing.

Perhaps trying the webcam without internet connected to the computer. 

iAtari

I disabled the Internet and this made no difference.It still give me the same error message.

---

### Post by irv on 2007-11-08
Is it possible that a config file got changed when I upgrade to 7.10? I am not sure what config file is used by a quick cam? Does any one have an idea?
Irv

---

### Post by harold4 on 2007-11-08
I remember having an issue similar.  I grabbed the newest gspca source, compiled the kernel module and all was well on the video side.

I'm still looking for a microphone resolution.

---

### Post by Skrim on 2007-11-09
I can't seem to get QuickCam to work either. Tried the latest gspca source without much luck. Not entirely sure if it stopped working after I upgraded to Gutsy or later though.

Update: Blacklisting v4l1_compat in /etc/modprobe.d/blacklist did the trick for me.

---

