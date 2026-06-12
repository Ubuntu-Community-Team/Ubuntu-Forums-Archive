---
title: "Modprobe fails when trying to eneble driver"
date: 2015-08-25
forum: Hardware
---

### Post by einsiol on 2015-08-25
I've been following the instructions on [this post]("http://http://ubuntuforums.org/showthread.php?t=2168426&p=12951929#post12951929") to enable my USB Wlan (DWA-171). The instructions are: 

```
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au
```

So far I had been able to rebuild the driver fine and enable it after each dist-upgrade when needed. For what I can tell the output from the "make" looks fine, nothing I can see difference and no errors, just few warnings like mention in the previous post. But when I try to enable it with the last command _sudo modprobe 8812au_ I get the following error:

> modprobe: ERROR: could not insert '8812au': Exec format error

What I've tried to do is copying a fresh version of the git repository and tried the build it again. I posted a question on the old thread above where it was recommended that I ran _sudo apt-get --reinstall install linux-image-$(uname -r)_ and try to build it again but with no luck.

I'm not sure what to do at this point and hope that anyone can get me on the right track. I'm running UbuntuGnome 15.04. The issue started soon after doing apt-get autoclean/autoremove, not directly after dist-update and reboot. But I'm not perfectly sure.

---

### Post by chili555 on 2015-08-25
> The issue started soon after doing apt-get autoclean/autoremove, not directly after dist-update and reboot. But I'm not perfectly sure.I wonder if something has gone wrong there. Let's try:```
sudo apt-get update
sudo apt-get -y dist-upgrade
```Unless this process changes or installs nothing at all, reboot. Then:```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
sudo apt-get install --reinstall build-essential
```Now, let's try again:```
cd ~/[COLOR="#FF0000"]Downloads[/COLOR]/rtl8812AU_8821AU_linux
```...or wherever you cloned the repository:```
make clean
make
sudo make install
sudo modprobe 8812au
```Any improvement?

---

### Post by einsiol on 2015-08-25
Hey [**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=35909"), following your instructions above ends with the same result, same error. "Exec format error".

There are no new updates as I have already upated everything, for the other commands the results are:

```
sudo apt-get install --reinstall linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/2.288 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 331462 files and directories currently installed.)
Preparing to unpack .../linux-headers-generic_3.19.0.27.26_amd64.deb ...
Unpacking linux-headers-generic (3.19.0.27.26) over (3.19.0.27.26) ...
Setting up linux-headers-generic (3.19.0.27.26) ...
```


```
sudo apt-get install --reinstall linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/764 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 331462 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.19.0-27-generic_3.19.0-27.29_amd64.deb ...
Unpacking linux-headers-3.19.0-27-generic (3.19.0-27.29) over (3.19.0-27.29) ...
Setting up linux-headers-3.19.0-27-generic (3.19.0-27.29) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.19.0-27-generic /boot/vmlinuz-3.19.0-27-generic
```

```
sudo apt-get install --reinstall build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 4.838 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://is.archive.ubuntu.com/ubuntu/ vivid/main build-essential amd64 11.6ubuntu6 [4.838 B]
Fetched 4.838 B in 0s (106 kB/s)           
(Reading database ... 331462 files and directories currently installed.)
Preparing to unpack .../build-essential_11.6ubuntu6_amd64.deb ...
Unpacking build-essential (11.6ubuntu6) over (11.6ubuntu6) ...
Setting up build-essential (11.6ubuntu6) ...
```


I don't know if it's relevant or not but I can add the warnings I get during the build process, but I can't tell if it's any different then the warnings I got before when I had no issues since I never saved them.

```
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c: In function ‘cfg80211_rtw_connect’:
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:2615:14: warning: assignment discards ‘const’ qualifier from pointer target type
    src_bssid = sme->bssid;
              ^
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c: At top level:
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5083:2: warning: initialization from incompatible pointer type
  .get_station = cfg80211_rtw_get_station,
  ^
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5083:2: warning: (near initialization for ‘rtw_cfg80211_ops.get_station’)
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5112:2: warning: initialization from incompatible pointer type
  .del_station = cfg80211_rtw_del_station,
  ^
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5112:2: warning: (near initialization for ‘rtw_cfg80211_ops.del_station’)
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5113:2: warning: initialization from incompatible pointer type
  .change_station = cfg80211_rtw_change_station,
  ^
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:5113:2: warning: (near initialization for ‘rtw_cfg80211_ops.change_station’)
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c: In function ‘rtw_cfg80211_inform_bss’:
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/ioctl_cfg80211.c:474:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/rtw_android.o
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/rtw_android.c: In function ‘rtw_android_priv_cmd’:
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/rtw_android.c:557:61: warning: passing argument 1 of ‘get_int_from_command’ makes pointer from integer without a cast
    pwfd_info->rtsp_ctrlport = ( u16 ) get_int_from_command( priv_cmd.buf );
                                                             ^
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/rtw_android.c:311:5: note: expected ‘char *’ but argument is of type ‘compat_uptr_t’
 int get_int_from_command(char* pcmd )
     ^
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/rtw_android.c:577:62: warning: passing argument 1 of ‘get_int_from_command’ makes pointer from integer without a cast
    pwfd_info->wfd_device_type = ( u8 ) get_int_from_command( priv_cmd.buf );
                                                              ^
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/rtw_android.c:311:5: note: expected ‘char *’ but argument is of type ‘compat_uptr_t’
 int get_int_from_command(char* pcmd )
     ^
/home/einar/Gits/rtl8812AU_8821AU_linux/rtl8812AU_8821AU_linux/os_dep/linux/rtw_android.c:601:20: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
   if (copy_to_user((void *)priv_cmd.buf, command, bytes_written)) {
                    ^
```

---

### Post by chili555 on 2015-08-25
Is this a new clone of the git in the last few days? Does 'make' end like this?```
Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/chili/Desktop/Forum/rtl8812AU_8821AU_linux/8812au.mod.o
  LD [M]  /home/chili/Desktop/Forum/rtl8812AU_8821AU_linux/8812au.ko
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-27-generic'

```Or similar?

May I see:```
uname -a
```

I get similar errors when I compile the driver on my system, but it modprobes without complaint.

---

### Post by einsiol on 2015-08-25
I did delete the old clone and cloned a fresh version from the repository just to be 100% sure. 

Yes, I get the same result in the end of the build process.

The info from my uname -a is:
```
Linux einar-laptop 3.19.0-27-generic #29-Ubuntu SMP Fri Aug 14 21:43:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by chili555 on 2015-08-25
I am temporarily out of ideas. I am carefully watching your raised issue: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux/issues/84](https://github.com/abperiasamy/rtl8812AU_8821AU_linux/issues/84)

Does the module load and work if you boot into an earlier kernel version at the GRUB menu? Can you just continue that way until the issue you raised is answered?

---

### Post by einsiol on 2015-08-26
I had tought that would work but it failed me as well, same result with the last kernel. I think this problem might be isolated to my self. I think I'll try to reformat my machine and try again since I really need this compointent to work ASAP. Thank you for your help

---

### Post by seba22 on 2015-09-17
Hello,

Did You give up? Does reinstall fix issue?

You are not alone and this is not a isolated issue, i have same problem here.

I had dkms configured to build and install rtl8812AU driver and few days after reboot it fail to wake up my wifi network card :/

Same as above
" modprobe 8812aumodprobe: ERROR: could not insert '8812au': Exec format error"

Can't tell what's make problem because my pc is turned on for over month... i apply all updates, kernel and don't reboot after...
So it can be something from month back that cause it stop working after reboot...

My kernel is:

3.19.0-28-generic



Any idea :>

PS: Someone could recommend usb card with similar performance 5ghz ac standard that will be without any problem out of box to ubuntu ? :>

Regards

---

