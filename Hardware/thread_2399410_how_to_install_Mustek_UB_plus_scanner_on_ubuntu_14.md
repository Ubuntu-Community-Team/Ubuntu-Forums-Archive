---
title: "how to install Mustek UB plus scanner on ubuntu 14,04 LTS?"
date: 2018-08-24
forum: Hardware
---

### Post by alchimisto on 2018-08-24
[ATTACH=CONFIG]280837[/ATTACH]

Hi everyone;

I followed instructions of this thread:

[https://ubuntuforums.org/showthread.php?t=154429](https://ubuntuforums.org/showthread.php?t=154429)

but it doesn&#8217;t work to install my "Mustek 1200 UB plus" from the beginning; the file isnt found, but I found it manually in "libsane" and did what follows but it doesn&#8217;t work, can you help my scanner get a second chance? I'm a begginer, you must explain me basics, and I'll follow all what you tell me to do :guitar:

---

### Post by kurt18947 on 2018-08-24
To start, I am no Ubuntu, Linux or scanner expert though I've had some experience. That thread is over 10 years old, I would not place too much confidence in it. Scanner support in Linux is provided by the SANE-project.org AFAIK. Here is a link to the Mustek page:

[URL="http://www.sane-project.org/sane-backends.html#S-MUSTEK-USB"]http://www.sane-project.org/sane-backends.html#S-MUSTEK-USB
                        [/URL][FONT=Calibri]

[SIZE=3]Edit: there may be some hope after all. You could look this over:
[/SIZE]
[http://manpages.ubuntu.com/manpages/bionic/man5/sane-mustek_usb.5.html](http://manpages.ubuntu.com/manpages/bionic/man5/sane-mustek_usb.5.html)
[/FONT] 

  [URL="http://www.sane-project.org/sane-backends.html#S-MUSTEK-USB"]
[/URL]

---

### Post by alchimisto on 2018-08-25
> **kurt18947 said:**
> To start, I am no Ubuntu, Linux or scanner expert though I've had some experience. That thread is over 10 years old, I would not place too much confidence in it. Scanner support in Linux is provided by the SANE-project.org AFAIK. Here is a link to the Mustek page:

[URL="http://www.sane-project.org/sane-backends.html#S-MUSTEK-USB"]http://www.sane-project.org/sane-backends.html#S-MUSTEK-USB
                        [/URL][FONT=Calibri]

[SIZE=3]Edit: there may be some hope after all. You could look this over:
[/SIZE]
[http://manpages.ubuntu.com/manpages/bionic/man5/sane-mustek_usb.5.html](http://manpages.ubuntu.com/manpages/bionic/man5/sane-mustek_usb.5.html)
[/FONT] 

  [URL="http://www.sane-project.org/sane-backends.html#S-MUSTEK-USB"]
[/URL]

Thank you very much, I appreciate it! but I'm really a beginner, and have to spend some time to understand those descriptions, I downloaded the firmware usb but I don't know how to install it... in the first link gt68xx is supposed to be in the folder sane etc but I found it eleswhere in /doc/libsane... and I did the required modifications but it doesn't work, so I hope I find someone who has still the same scanner as me now hmmmm :confused:

---

### Post by alchimisto on 2018-09-07
Finally worked for me because of this tuto :guitar:

[https://ssnjara.wordpress.com/2011/10/24/howto-install-mustek-1200-ub-plus-scanner-on-ubuntu-11-10/](https://ssnjara.wordpress.com/2011/10/24/howto-install-mustek-1200-ub-plus-scanner-on-ubuntu-11-10/)

---

