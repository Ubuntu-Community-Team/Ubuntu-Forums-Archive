---
title: "rpm to deb"
date: 2010-11-14
forum: Hardware
---

### Post by gnulab on 2010-11-14
Hi Guys,

I'm using HP Probook 4420s and my touchpad isn't working 100%.

I'm facing trouble with having 2 fingers on the touchpad simultaneously, thus I can't drag a window around. Nor can I do a right click.

On this website,
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=4145435&prodNameId=4145438&swEnvOID=2020&swLang=13&mode=2&taskId=135&swItem=ob-86384-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=4145435&prodNameId=4145438&swEnvOID=2020&swLang=13&mode=2&taskId=135&swItem=ob-86384-1)

HP provides driver for Linux, unfortunately it is for SUSE Linux disto. I have tried using alien to convert the .rpm to .deb, but this is the result I get when I try to install it via ```
sudo dpkg -i name-of-deb-file.deb
```The result is this:```

htw@htw-laptop:~/Downloads$ sudo dpkg -i synaptics-touchpad_15.1.4.0-13_i386.deb 
(Reading database ... 120324 files and directories currently installed.)
Preparing to replace synaptics-touchpad 15.1.4.0-13 (using synaptics-touchpad_15.1.4.0-13_i386.deb) ...
Unpacking replacement synaptics-touchpad ...
Setting up synaptics-touchpad (15.1.4.0-13) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for ureadahead ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
htw@htw-laptop:~/Downloads
```I want to give HP's touchpad driver a try and see if it works, but I'm stump what happen next. So anyone can guide me?

Thanks
Henry

---

