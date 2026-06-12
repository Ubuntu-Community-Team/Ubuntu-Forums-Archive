---
title: "How can I rollback my upgrades?"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by kayex on 2009-10-08
Hello,

I've recently done a 'aptitude safe-upgrade' in ubuntu jaunty, after which I rebooted and I am no longer able to access my RAID5 array (External SATA via a Highpoint RocketRaid Card).

I suspect it's related to the kernel upgrade below (from /var/log/aptitude):

> Aptitude 0.4.11.11: log report
Thu, Oct  8 2009 12:41:12 -0400

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 22 packages, and remove 0 packages.
508kB of disk space will be used
===============================================================================
[UPGRADE] libglib2.0-0 2.20.1-0ubuntu2 -> 2.20.1-0ubuntu2.1
[UPGRADE] libglib2.0-data 2.20.1-0ubuntu2 -> 2.20.1-0ubuntu2.1
[UPGRADE] libglib2.0-dev 2.20.1-0ubuntu2 -> 2.20.1-0ubuntu2.1
[UPGRADE] libpam-smbpass 2:3.3.2-1ubuntu3.1 -> 2:3.3.2-1ubuntu3.2
[UPGRADE] libsmbclient 2:3.3.2-1ubuntu3.1 -> 2:3.3.2-1ubuntu3.2
[UPGRADE] libsmbclient-dev 2:3.3.2-1ubuntu3.1 -> 2:3.3.2-1ubuntu3.2
[UPGRADE] libwbclient0 2:3.3.2-1ubuntu3.1 -> 2:3.3.2-1ubuntu3.2
[UPGRADE] linux-headers-2.6.28-15 2.6.28-15.49 -> 2.6.28-15.52
[UPGRADE] linux-headers-2.6.28-15-server 2.6.28-15.49 -> 2.6.28-15.52
[UPGRADE] linux-image-2.6.28-15-generic 2.6.28-15.49 -> 2.6.28-15.52
[UPGRADE] linux-image-2.6.28-15-server 2.6.28-15.49 -> 2.6.28-15.52
[UPGRADE] linux-libc-dev 2.6.28-15.49 -> 2.6.28-15.52
[UPGRADE] samba 2:3.3.2-1ubuntu3.1 -> 2:3.3.2-1ubuntu3.2
[UPGRADE] samba-common 2:3.3.2-1ubuntu3.1 -> 2:3.3.2-1ubuntu3.2
[UPGRADE] samba-doc 2:3.3.2-1ubuntu3.1 -> 2:3.3.2-1ubuntu3.2
[UPGRADE] samba-tools 2:3.3.2-1ubuntu3.1 -> 2:3.3.2-1ubuntu3.2
[UPGRADE] smbclient 2:3.3.2-1ubuntu3.1 -> 2:3.3.2-1ubuntu3.2
[UPGRADE] smbfs 2:3.3.2-1ubuntu3.1 -> 2:3.3.2-1ubuntu3.2
[UPGRADE] tzdata 2009m-0ubuntu0.9.04 -> 2009n-0ubuntu0.9.04
[UPGRADE] wget 1.11.4-2ubuntu1 -> 1.11.4-2ubuntu1.1
[UPGRADE] winbind 2:3.3.2-1ubuntu3.1 -> 2:3.3.2-1ubuntu3.2
===============================================================================How can I rollback the upgrades above?

Thank you

---

### Post by slakkie on 2009-10-09
Kernels are not removed after an upgrade, so you can boot back into the old kernel, unless it is a minor revision upgrade.

```

dpkg -l | grep linux-image

```

This will list all your installed kernels. If there is only one kernel listed, then you might have a minor revision upgrade.

[UPGRADE] linux-image-2.6.31-12-generic 2.6.31-12.40 -> 2.6.31-12.41

If you see upgrades like these:

[UPGRADE] linux-image-generic 2.6.31.11.22 -> 2.6.31.12.23

Then the -11 kernel will be present and you can boot into that one.

If you don't have any other kernels expect for the running one you can do one of the following things:

```

aptitude search linux-image

```

And install another kernel and boot into that one:

```

p   linux-image-2.6.28-11-generic   - Linux kernel image for version 2.6.28 on x
p   linux-image-2.6.28-13-generic   - Linux kernel image for version 2.6.28 on x
p   linux-image-2.6.28-14-generic   - Linux kernel image for version 2.6.28 on x
p   linux-image-2.6.28-15-generic   - Linux kernel image for version 2.6.28 on x

```

Install one of these or..

You could run apt-cache policy linux-image-generic and see if there is another version available in the main repos, because those upgrades are most likely -updates, so you could then force a re-installation of your kernel.
For jaunty (i'm doing this on a karmic install, so you'll see an installed kernel which is not available to you).

```

linux-image-generic:
  Installed: 2.6.31.12.23
  Candidate: 2.6.31.12.23
  Version table:
 *** 2.6.31.12.23 0
        100 /var/lib/dpkg/status
     2.6.28.15.20 0
        550 http://security.ubuntu.com jaunty-security/main Packages
        550 http://nl.archive.ubuntu.com jaunty-updates/main Packages
     2.6.28.11.15 0
        550 http://nl.archive.ubuntu.com jaunty/main Packages

```

So you would install the 2.6.28.11.15 version of the linux-image-generic package

```

# Remove -s, simulate option
sudo aptitude -s install  linux-image-generic=2.6.28.11.15
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages will be DOWNGRADED:
  linux-image-generic
The following NEW packages will be installed:
  linux-image-2.6.28-11-generic
0 packages upgraded, 1 newly installed, 1 downgraded, 0 to remove and 8 not upgraded.
Need to get 24.6MB of archives. After unpacking 95.7MB will be used.
Do you want to continue? [Y/n/?] y
Would download/install/remove packages.

```


After that you will need to remove the old kernel:

```

rmkernel () {
        local cur_kernel=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
        local kernel_pkg="linux-(image|headers|ubuntu-modules|restricted-modules)"
        local meta_pkg="${kernel_pkg}-(generic|i386|server|common|rt|xen|ec2)"
        sudo aptitude purge $(dpkg -l | egrep $kernel_pkg | egrep -v "${cur_kernel}|${meta_pkg}" | awk '{print $2}')
        purge_pkg
}

```

And you need to pin the linux-image-generic package:

```

pkg2pin () {
        [ -z "$1" ] && return
        local pkg
        local msg
        msg="$(date +'%Y%m%d:%H%M%S')"
        for pkg in $@
        do
                pkg=$(dpkg -l "$pkg" 2>/dev/null)
                [ $? -ne 0 ] && continue
                pkg=$(echo -e "$pkg" | grep "^ii" |awk '{print $2" "$3}')
                echo -e "$pkg" | awk '{print "Explanation: Added on '$msg' by pkg2pin or dpkg2pin\nPackage: "$1"\nPin: version "$2"\nPin-Priority: 1001\n"}'
        done | sudo tee -a /etc/apt/preferences
}
dpkg2pin () {
        [ -z "$1" ] && return
        local pkg
        pkg=$(dpkg -l | grep "^ii" |awk '{print $2}' | grep "$1")
        [ $? -ne 0 ] && return
        for i in $pkg
        do
                pkg2pin $i
        done
}

```

Put this rmkernel, pkg2pin and dpkg2pin code in your .bashrc and source your bashrc file (source ~/.bashrc) and then you can run the commands:

```

rmkernel
dpkg2pin linux-image-generic

```

Now your kernel will not be upgraded anymore, unless you remove the /etc/apt/preferences file.

---

### Post by iGadget2 on 2009-10-09
Well, slakkie sure put in a lot of code there. :)

If this machine is running a GUI, you might also consider this (guru's, please correct me if I'm wrong):
-Run Synaptic
-Find the kernel package that you know to be working and select it
-Select the 'pin package' option from the Package menu (I'm not sure about the English translation, I'm using Dutch here)
-Now just to make sure this kernel is loaded at startup, you'll have to change a few settings in your GRUB config:

[LIST]
[*]Edit /boot/grub/menu.lst as root
[*]change 'default 0' to 'default saved'
[*]add 'savedefault' (without quotes) just below the boot entry of the specific kernel (usually somewhere at the end of the menu.lst file)
[*]Save the file
[/LIST]
Next time when you reboot and select this kernel from the GRUB menu, it will be the default selected kernel at boot.

---

