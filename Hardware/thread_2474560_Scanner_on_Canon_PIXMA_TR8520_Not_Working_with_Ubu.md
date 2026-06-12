---
title: "Scanner on Canon PIXMA TR8520 Not Working with Ubuntu 22.04"
date: 2022-05-02
forum: Hardware
---

### Post by nbmota on 2022-05-02
Hello,

I have a multi-function device that does scanning, printing, copying and fax sending. It is a small Canon PIXMA TR8520 small desktop machine. Both its printing and scanning functionalities were working fine in conjunction with Ubuntu Linux 20.04 and with Ubuntu Linux 20.10. Yet, now that I have upgraded to Ubuntu Linux 22.04 it does not work.

According to the SANE (Scanner Access Now Easy) project's website, I need a driver called sane-escl.5 in order to get the scanning functionality of my device to work. You can find that information in the following web-page: [http://sane-project.org/man/sane-escl.5.html](http://sane-project.org/man/sane-escl.5.html). Ubuntu Linux's manual provides a link to download that file in a compressed file format. That compressed file is called [sane-escl.5.gz]("http://manpages.ubuntu.com/manpages.gz/jammy/man5/sane-escl.5.gz"). It also provices a link to download an executable file that has a package library that also contains this driver. That package library is called [libsane-common_1.1.1-5_all]("https://launchpad.net/ubuntu/jammy/+package/libsane-common").deb. You can find both of those downloads links at: [http://manpages.ubuntu.com/manpages/jammy/en/man5/sane-escl.5.html#authors](http://manpages.ubuntu.com/manpages/jammy/en/man5/sane-escl.5.html#authors).

I tried downloading both files off of Ubuntu Linux's Manual's website. Then, I tried installing the sudo apt install ./libsane-common_1.1.1-5_all.deb using the following command:
**[B]:$ **[/B]```
sudo apt install ./libsane-common_1.1.1-5_all.deb
```

However, I received an output that basically said that its equivalent was already installed. It said the following:
[B]Note, selecting 'libsane-common' instead of './libsane-common_1.1.1-5_all.deb'
libsane-common is already the newest version (1.1.1-5).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/B]

This would be fine, if I could access my scanner. Yet, after that, I installed the *document-imaging* app using the AppStore to see if I could and, I was unable to. I tried to start the *document-imaging* app by calling it through the terminal, just by entering its name like this:

**:$ **```
document-imaging
```

And then pressing the ENTER key. Yet, I got the following error message:

[B]warning: Could not find config file in /home/me/snap/document-imaging/11/scanner.json
warning: Could not find config file in /home/me/snap/document-imaging/11/metadata.json
Cannot find scanner![/B]

I also tried installing the SkanLite app, which has a GUI (Graphical User Interface) to see if I could access my scanner through it. Yet, when I started the SkanLite, it gave me an error as well. The error was as follows:

"The SANE (Scanner Access Made Easy) could not find any device. Check that your scanner is plugged in and turned on or check your scanner setup."

My scanner had been plugged in, connected to my computer and turned on when I tried both of these apps to see if I could access it. Yet neither of them worked!

I also tried decompressing the [sane-escl.5.gz]("http://manpages.ubuntu.com/manpages.gz/jammy/man5/sane-escl.5.gz") file to see if I could install the driver manually. I did this by using the following command in the terminal:

**:$** ```
gzip -d sane-escl.5.gz
```

Decompressing that archive placed the file sane-escl.5 in the directory that I was in. Yet, I do not know where I am supposed to place it so that this driver will be installed! Perhaps at on of the following locations:
[LIST]
[*]/etc/sane.d/ 
[*]_/usr/lib/x86_64-linux-gnu/sane/_ 
[/LIST]

Yet, I do not know where to place this driver file to get it installed for sure.

Then, I tried to uninstall libsane-common so that I could install the slightly different version of libsane-common that I downloaded from Ubuntu's Manual's website that would not install because I already had a version of this software package installed. I did this by typing in the following command in the terminal:

**:$ **```
sudo apt remove libsane-common
```

It uninstalled successfully.

After that, I tried installing the libsane-common_1.1.1-5_all.deb package again by typing the following command on the terminal:

**:$ **```
sudo apt install ./libsane-common_1.1.1-5_all.deb
```

It installed successfully. However, when I tried to access my scanner using the document-imaging app, I got the same error once again and my computer was unable to communicate with it. When I tried to access it using the SkanLite app, that app also gave me the same error that it had previously given me and could not find my scanner.

I still have a feeling that if I knew the correct folder to place the file sane-escl.5, that there is a strong possibility that moving that file to the right directory would solve my problem and enable me to have scanner access once in this new version of Ubuntu Linux. Could anybody help me to install my scanner's driver?

I would really appreciate it!

---

### Post by brian_p on 2022-05-03
> **nbmota said:**
> Hello,

I have a multi-function device that does scanning, printing, copying and fax sending. It is a small Canon PIXMA TR8520 small desktop machine. Both its printing and scanning functionalities were working fine in conjunction with Ubuntu Linux 20.04 and with Ubuntu Linux 20.10. Yet, now that I have upgraded to Ubuntu Linux 22.04 it does not work.

There are significant printing and scanning enhancements on Ubuntu 22.04 compared with the previous two distros, particularly concerning USB connections. Are you on USB?

None of the actions you took should have been necessary because 22.04 is designed to set up printing and scanning on USB and wireless **automatically**  .

Give ```
systemctl status ipp-usb
```

```
scanimage -L
```

```
airscan-discover
```

---

