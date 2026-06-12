---
title: "How do I switch nvidia driver to nouveau again in terminal?"
date: 2015-03-22
forum: Hardware
---

### Post by Novitk on 2015-03-22
Hello, I have a dell notebook with 2 video cards, intel integrated and nvidia geforce gt 730m. I'm about to change my nouveau driver to the nvidia-331 proprietary driver graphically using this gui:

[IMG]http://www.imageupload.co.uk/images/2015/03/22/Screenshotfrom2015-03-22031742.png[/IMG]

But I'm afraid my system will break down after I reboot and I won't be able to return to nouveau driver using this GUI again, since my graphics will be down and I'll only be able to initialize the system in terminal (text mode, without graphic support). My question is: if my system breaks down after the driver change, how do I switch nvidia driver to nouveau again in terminal?

---

### Post by dino99 on 2015-03-22
the easiest and cleanest way is to purge the installed driver and then install the 'nouveau' driver

sudo apt-get purge nvidia*
sudo apt-get install xserver-xorg-video-nouveau

---

### Post by ajgreeny on 2015-03-22
I think the nouveau driver is installed by default so there will be no need to install it, you will simply need to remove the nvidia driver as 9d9 says.

You will probably get an error when trying to run the install the xserver-xorg-video-nouveau command as it will already be installed.

---

### Post by Novitk on 2015-03-22
Thanks, guys!

---

