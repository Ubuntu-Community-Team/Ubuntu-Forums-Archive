---
title: "No sound when headphones are plugged in"
date: 2010-08-24
forum: Hardware
---

### Post by GreggyZed on 2010-08-24
Hi,

I have recently purchased a Asus eeepc 1001p and have installed Ubuntu Netbook Remix.  I am having a few issues (such as getting the hotkeys to work, disabling the touchpad when typing, and enabling multi-touch) but overall I am quite pleased with how things have turned out.

However, the sound works fine from the onboard speakers, but when I plug in headphones, there is no sound through them (but the on-board speakers do mute as they should).  I went through the steps of the Alsa update script that I saw elsewhere on this forum and it did not change anything.

Also, there is no headphone section when running Alsamixer.  I'm not sure if this is part of the issue or not, it is just something I've noticed.

If you have any ideas on what could be causing this problem, I would be very grateful.  I hope to get this working so I can move on to the less pressing issues.

Greg

---

### Post by lidex on 2010-08-26
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by GreggyZed on 2010-08-26
When I ran it, the first tone played fine, but then the program just hung without playing the tone that is supposed to switch between channels until I eventually force quit it.

---

### Post by lidex on 2010-08-28
Did you submit a bug report?

---

### Post by GreggyZed on 2010-08-28
The bug reporting program never gets far enough to do so.

---

### Post by lidex on 2010-08-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by GreggyZed on 2010-08-28
The output is located here:

[http://www.alsa-project.org/db/?f=39c04ba8b17214f5ee2cb9d64af369020c65e192](http://www.alsa-project.org/db/?f=39c04ba8b17214f5ee2cb9d64af369020c65e192)

---

### Post by lidex on 2010-08-28
That quirk you added to alsa-base.conf isn't working. Try changing the model. Choose from these options:
```
basic
auto
lifebook

```

You didn't mention you had edited that file.

---

### Post by GreggyZed on 2010-08-28
Sorry, the problem existed before I edited that file and I thought I had changed it back to auto.  I tried all 3 options and none of them worked so I set it back to model=auto.

---

### Post by lidex on 2010-08-29
OK. Remove all options from alsa-base.conf and try the ```
ubuntu-bug audio
``` command again.

---

### Post by GreggyZed on 2010-08-29
> **GreggyZed said:**
> When I ran it, the first tone played fine, but then the program just hung without playing the tone that is supposed to switch between channels until I eventually force quit it.

I tried it twice and both times this occurred again.

---

### Post by lidex on 2010-08-29
Bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183)
Please go there.

---

### Post by GreggyZed on 2010-08-29
On that page, Pablo's fix seemed to work, which was actually your fix since it was to change the line as lifebook.  I really have no idea what I did wrong when you asked me to do it, but now it's working and I'd like to thank you for all of your help.  I greatly appreciate it.

---

### Post by lidex on 2010-08-29
Who knows? What's important is you're up and running and have more knowledge than you did before. A good day then! Glad to help.

---

