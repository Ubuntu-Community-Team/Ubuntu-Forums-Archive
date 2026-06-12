---
title: "HD 7870 driver problem ubuntu 16.04.2"
date: 2017-07-16
forum: Hardware
---

### Post by lallapallochax on 2017-07-16
Hello everybody,
I have recently installed ubuntu 16.04.2 on my computer thinking everything would be fine but i got wrong: the drivers of my vga:HD 7870 aren't listed on additional drivers and i experience low performances.I tried to install them with this procedure: [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)
they don't appear anyway...running the command: dpkg -l amdgpu-pro i get this:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  amdgpu-pro     17.10-450821 amd64        Meta package to install amdgpu Pr

```
I was thinking that ubuntu uses the integrated vga of my cpu instead of my vga.May it be an idea?
My specs(if could be useful)
i5 6600
HD 7870
asrock h170 pro4s
8 gb of ram


this is what appears in additional drivers: 
[IMG]http://i66.tinypic.com/14keakh.png[/IMG]

Thanks for the help

---

### Post by QIII on 2017-07-16
Hello!

The HD 7800 series are supposed to be supported by AMDGPU-PRO now.

Did you try to reinstall?  I would give that a try first.  Your link provides the command to uninstall ```
amdgpu-pro-uninstall
```  When you have done that carefully follow the installation instructions again.  If that does not work, let us know.  AMDGPU may not have been installed if the Ubuntu installer did not recognize the 7800 as supported when you installed.  That may be the issue.

Don't worry about the additional drivers message.  That is for your CPU.  There is no additional driver for your GPU.  On install, AMDGPU is installed for supported hardware.  AMDGPU-PRO, the proprietary overlay, is not in thr repo for now.

---

### Post by lallapallochax on 2017-07-18
> **QIII said:**
> Hello!

The HD 7800 series are supposed to be supported by AMDGPU-PRO now.

Did you try to reinstall?  I would give that a try first.  Your link provides the command to uninstall ```
amdgpu-pro-uninstall
```  When you have done that carefully follow the installation instructions again.  If that does not work, let us know.  AMDGPU may not have been installed if the Ubuntu installer did not recognize the 7800 as supported when you installed.  That may be the issue.

Don't worry about the additional drivers message.  That is for your CPU.  There is no additional driver for your GPU.  On install, AMDGPU is installed for supported hardware.  AMDGPU-PRO, the proprietary overlay, is not in thr repo for now.



Hi,thanks for the reply first
I've tried to reinstall it several times but same results..
I'm not expert towards linux stuff but..could be possible as you say that the vga drivers get installed and work also but they don't appear in additional drivers?How could i check if they are working or not?:confused: sorry for the dumb question
I get this doubt because i saw a tutorial on how to install those drivers in which the video maker says" if you get this massage everything has gone good " i get the same message typing the command
[IMG][IMG]http://i66.tinypic.com/oscuom.png[/IMG][/IMG]

thanks

---

### Post by lallapallochax on 2017-07-20
Woah,
Switched from Ubuntu gnome to Ubuntu and installed driver again:before in system information was written "gallium etc" now "HD 7800" i think this is the proof that drivers are installed
Thank you anyway :D

---

