---
title: "Remix 9.04 or full desktop version on EPC 1000HE"
date: 2009-05-02
forum: Hardware
---

### Post by tcman on 2009-05-02
I just purchased the EPC 1000HE. 
I would like to load the newest 9.04, but noticed there is a "Remix 9.04" specially for netbooks vs the desktop version.  

Does anyone know what the major differences are between the two and why I should load one over the other?  Would it cause any problems if I loaded the desktop version on my netbook?

Or just point me to documentation.  The docs I've read so far are all marketing created and just paint a rosy picture of both but give little or no details on the differences.

Thanks in advance.

---

### Post by kerry_s on 2009-05-02
depends hows your linux knowledge?

just try them all:
[http://www.eeebuntu.org/](http://www.eeebuntu.org/)

---

### Post by surfed on 2009-05-02
> **tcman said:**
> I just purchased the EPC 1000HE. 
I would like to load the newest 9.04, but noticed there is a "Remix 9.04" specially for netbooks vs the desktop version.  

Does anyone know what the major differences are between the two and why I should load one over the other?  Would it cause any problems if I loaded the desktop version on my netbook?

Or just point me to documentation.  The docs I've read so far are all marketing created and just paint a rosy picture of both but give little or no details on the differences.

Thanks in advance.


The difference is in the interface and you can switch between NBR and regular Desktop.

---

### Post by tcman on 2009-05-02
Hi surfed,

so there's no difference "under the hood"?  Only in the front end gui?

---

### Post by tcman on 2009-05-02
> **kerry_s said:**
> depends hows your linux knowledge?

just try them all:
[http://www.eeebuntu.org/](http://www.eeebuntu.org/)

Hi kerry_s,

I know enough about OS's to do installs, but my experience is mostly in MS and main frame world.  My personal desktop is a dual boot system of Vista and Ubuntu 8.04.  My issue is I don't have the time to try them all, so just trying to get some info to streamline my decision on which one to install.

Thanks.

---

### Post by ChinFurr on 2009-05-02
I do have a 1000HE running the new NBR of 9.04 and it seems to be running fine in terms of hardware. There is an option in System -> Preferences -> Switch Desktop Modes that allows you to go to traditional desktop if you don't like the new clutter type. The only thing you need to do is disable the Maximus demon in System -> Preferences -> Startup Applications and make the switch. One error though that has been getting me is that the desktop has issues where it does not display items in ~/Desktop or render any icons on the actual desktop background. Don't know if it's a bug or a setting, I'm still poking around though. Otherwise the NBR with Ext4 has been pretty nice.

---

### Post by surfed on 2009-05-02
When trying to install Netbook Rimix via Synaptic on a regular install the following packages are being pulled in as dependencies:

```

The following NEW packages will be installed:
  app-install-data-commercial cellwriter cheese desktop-switcher fbreader
  gnome-netstatus-applet gnome-themes go-home-applet human-netbook-theme
  libclutter-0.8-0 libclutter-gtk-0.8-0 libfakekey0 libzlcore-data
  libzlcore0.9 libzltext0.9 libzlui-gtk maximus netbook-launcher
  ubuntu-netbook-remix ubuntu-netbook-remix-default-settings webfav
  window-picker-applet xautomation xserver-xorg-input-evtouch
0 upgraded, 24 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by mikedep333 on 2009-05-03
> **surfed said:**
> When trying to install Netbook Rimix via Synaptic on a regular install the following packages are being pulled in as dependencies:

```

The following NEW packages will be installed:
  app-install-data-commercial cellwriter cheese desktop-switcher fbreader
  gnome-netstatus-applet gnome-themes go-home-applet human-netbook-theme
  libclutter-0.8-0 libclutter-gtk-0.8-0 libfakekey0 libzlcore-data
  libzlcore0.9 libzltext0.9 libzlui-gtk maximus netbook-launcher
  ubuntu-netbook-remix ubuntu-netbook-remix-default-settings webfav
  window-picker-applet xautomation xserver-xorg-input-evtouch
0 upgraded, 24 newly installed, 0 to remove and 0 not upgraded.
```

Surfed:

Installing dependencies is very common and almost completely harmless. I don't see any issues with you installing those packages.

Tcman: The big difference is that the netbook remix installs a few more applications by default, is optimized for small screens, and is optimized for doing one or a few tasks at once (it's a netbook after all.)

You really can't go wrong with either one.

---

### Post by tcman on 2009-05-03
> **mikedep333 said:**
> Surfed:

Installing dependencies is very common and almost completely harmless. I don't see any issues with you installing those packages.

Tcman: The big difference is that the netbook remix installs a few more applications by default, is optimized for small screens, and is optimized for doing one or a few tasks at once (it's a netbook after all.)

You really can't go wrong with either one.

Ok, I took the plunge.  I loaded my epc1000he with Remix 9.04 at 100%, and not dual boot with MS.  Most major things seem to be working fine.  I really like the new layout, but have to get use to the new layout.

Thanks for everyone's help and advice.

---

### Post by FatherDale on 2009-05-04
> **tcman said:**
> Ok, I took the plunge.  I loaded my epc1000he with Remix 9.04 at 100%, and not dual boot with MS.  Most major things seem to be working fine.  I really like the new layout, but have to get use to the new layout.

Thanks for everyone's help and advice.

Good for you. It's useful because it's been optimized for the 1024x600 screen. There's a script over at [http://forum.eeeuser.com/viewtopic.php?id=65606](http://forum.eeeuser.com/viewtopic.php?id=65606) that will make your function keys work without too much pain. I'm sure there's more I can do to this thing, but it's pretty useful now, don't want to mess with it until it's broke... :)

---

