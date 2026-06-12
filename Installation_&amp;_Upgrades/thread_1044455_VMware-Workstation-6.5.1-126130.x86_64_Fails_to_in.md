---
title: "VMware-Workstation-6.5.1-126130.x86_64 Fails to install!!!"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by Dr Zin on 2009-01-19
So I went to the VMware site and download a copy of VMware-Workstation-6.5.1-126130.x86_64. So it come in RPM file ok so I go to the  Ubuntu page where it talks about change the file to readable file so I could install. 

```
drzin@deathcom:~$ sudo alien /home/drzin/Downloads/VMware-Workstation-6.5.1-126130.x86_64.rpm
Warning: Skipping conversion of scripts in package VMware-Workstation: postinst prerm
Warning: Use the --scripts parameter to include the scripts.






^C

```

I tried it with Kpackage. This is the out put.

```
smart install -y  /home/drzin/Downloads/VMware-Workstation-6.5.1-126130.x86_64.rpm ;echo RESULT=$?
Loading cache...
error: Unable to create channel for file: /home/drzin/Downloads/VMware-Workstation-6.5.1-126130.x86_64.rpm

RESULT=1
 

```

I have Vbox installed. But i am limited I could used that for. I am going to Vbox to build images.

---

