---
title: "setpci problem"
date: 2011-03-02
forum: Hardware
---

### Post by ianc1 on 2011-03-02
My laptop brightness controls (Fn_F8 and Fn-F9) don't work its using a VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03).  The brightness applet indicates the changes and I can see level changes being written to files.  This issue doesn't bother me too much as I can change it using ```
sudo setpci -s 00:02.0 F4.B=value
```I set to run off two icons for low brightness (value =50) and max brightness (value = ff).  At first the use of the root password for this didn't bother me but now it does.  So I made to bash scripts for this, simple one liners and called them low-brightness.sh and max-brightness.sh made them executable (chmod +x ....) and owned by root (chown root ....).  They are stored in my ~/bin directory which is in the path.
I added the lines ```
username ALL = NOPASSWD: /home/username/bin/low-brightness.sh
``````
username ALL = NOPASSWD: /home/username/bin/low-brightness.sh
```to my sudoers file using visudo.  Now when I run the files from an icon or the terminal I get the following error:
pcilib: Cannot open /sys/bus/pci/devices/0000:00:02.0/config

Any ideas would be much appreciated if a sudo the .sh file name I get the error command not found.

Sorry for the lengthy post.

Any help will be much appreciated.

---

### Post by pihbar on 2011-05-15
Your script calls the protected executable setpci. What you need to do is something like

```
username ALL = NOPASSWD: /usr/bin/setpci
```

and also possibly chmod some directories (which are listed as unreachable when you try to run setpci...).

---

### Post by ianc1 on 2011-05-15
Thanks pihbar.

Is it advisable to allow all users to access /usr/bin/setpci without password or the directories suggested?  I assume they have these permissions for a reason.  I thought my script would permit just access to setpci by myself.

Thanks

---

