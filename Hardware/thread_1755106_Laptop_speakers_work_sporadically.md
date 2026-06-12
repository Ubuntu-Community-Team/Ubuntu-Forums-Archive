---
title: "Laptop speakers work sporadically"
date: 2011-05-10
forum: Hardware
---

### Post by OlyPerson on 2011-05-10
I have a Samsung Q430 running 11.04 and I'm having an issue where the internal speakers only work every few boot-ups (same thing happened with 10.10, but with 10.04 they just never worked).  If I log in and out sometime they will work, but I find no rhyme or reason they don't work most of the time.

I've tried restarting pulseaudio, but I'm not really all that sure what I'm doing.  Can anyone help me?

Thanks for any help, just a big annoyance with this laptop and Ubuntu.

---

### Post by lidex on 2011-05-10
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Next use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

