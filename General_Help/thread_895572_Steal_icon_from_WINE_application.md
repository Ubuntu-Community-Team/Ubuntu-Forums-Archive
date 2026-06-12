---
title: "Steal icon from WINE application"
date: 2008-08-20
forum: General Help
---

### Post by altonbr on 2008-08-20
I installed MSN Messenger 7.0 so I could steal its icon but I can't seem to find where it is sitting.

I copied the launcher to the desktop and the .desktop looks like this:
```
[Desktop Entry]
Name=MSN Messenger 7.0
Exec=env WINEPREFIX="/home/brett/.wine" wine "C:\\Program Files\\MSN Messenger\\msnmsgr.exe"
Type=Application
StartupWMClass=Wine
Comment=Shows whether your friends are online and lets you have online conversations.
Icon=561c_msblico
```

I've done a search for '561c_msblico' but to no avail. Where/how can I copy this icon, or any WINE icon in general?

---

### Post by LowSky on 2008-08-20
[http://images.google.com/imgres?imgurl=http://www.iconarchive.com/icons/nelson/msn-buddy-icons/icons.jpg&imgrefurl=http://www.iconarchive.com/category/system/msn-buddy-icons-icons-by-nelson.html&h=286&w=708&sz=40&hl=en&start=2&um=1&tbnid=4_qrQhu1mGvKZM:&tbnh=57&tbnw=140&prev=/images%3Fq%3Dmsn%2Bim%2Bicon%26um%3D1%26hl%3Den%26sa%3DN](http://images.google.com/imgres?imgurl=http://www.iconarchive.com/icons/nelson/msn-buddy-icons/icons.jpg&imgrefurl=http://www.iconarchive.com/category/system/msn-buddy-icons-icons-by-nelson.html&h=286&w=708&sz=40&hl=en&start=2&um=1&tbnid=4_qrQhu1mGvKZM:&tbnh=57&tbnw=140&prev=/images%3Fq%3Dmsn%2Bim%2Bicon%26um%3D1%26hl%3Den%26sa%3DN)

---

### Post by altonbr on 2008-08-20
> **LowSky said:**
> [http://images.google.com/imgres?imgurl=http://www.iconarchive.com/icons/nelson/msn-buddy-icons/icons.jpg&imgrefurl=http://www.iconarchive.com/category/system/msn-buddy-icons-icons-by-nelson.html&h=286&w=708&sz=40&hl=en&start=2&um=1&tbnid=4_qrQhu1mGvKZM:&tbnh=57&tbnw=140&prev=/images%3Fq%3Dmsn%2Bim%2Bicon%26um%3D1%26hl%3Den%26sa%3DN](http://images.google.com/imgres?imgurl=http://www.iconarchive.com/icons/nelson/msn-buddy-icons/icons.jpg&imgrefurl=http://www.iconarchive.com/category/system/msn-buddy-icons-icons-by-nelson.html&h=286&w=708&sz=40&hl=en&start=2&um=1&tbnid=4_qrQhu1mGvKZM:&tbnh=57&tbnw=140&prev=/images%3Fq%3Dmsn%2Bim%2Bicon%26um%3D1%26hl%3Den%26sa%3DN)

Thanks, but that's not the official MSN logo. I'm looking for the official MSN and WLM logos.

---

### Post by editrix on 2008-08-21
When I searched for the one program I'm running under Wine I got this:

/home/username/.local/share/icons/b06c_imgburn.0.xpm
/home/username/.wine/drive_c/windows/temp/b06c_imgburn.0.xpm
/var/tmp/kdecache-username/favicons/forum.imgburn.com.png

The last, obviously, is a kde directory, but there should be an equivalent in Gnome.

---

### Post by kostkon on 2008-08-21
> **altonbr said:**
> I installed MSN Messenger 7.0 so I could steal its icon but I can't seem to find where it is sitting.

I copied the launcher to the desktop and the .desktop looks like this:
```
[Desktop Entry]
Name=MSN Messenger 7.0
Exec=env WINEPREFIX="/home/brett/.wine" wine "C:\\Program Files\\MSN Messenger\\msnmsgr.exe"
Type=Application
StartupWMClass=Wine
Comment=Shows whether your friends are online and lets you have online conversations.
Icon=561c_msblico
```

I've done a search for '561c_msblico' but to no avail. Where/how can I copy this icon, or any WINE icon in general?
Install *icoutils* and then to extract all the icon files from the *msnmsgr.exe* to your current directory, do
```
 wrestool -x --output=. -t14 ~/.wine/drive_c/Program\ Files/MSN\ Messenger/msnmsgr.exe
```
or something similar

---

### Post by altonbr on 2008-08-21
> **editrix said:**
> When I searched for the one program I'm running under Wine I got this:

/home/username/.local/share/icons/b06c_imgburn.0.xpm
/home/username/.wine/drive_c/windows/temp/b06c_imgburn.0.xpm
/var/tmp/kdecache-username/favicons/forum.imgburn.com.png

The last, obviously, is a kde directory, but there should be an equivalent in Gnome.

> **kostkon said:**
> Install *icoutils* and then to extract all the icon files from the *msnmsgr.exe* to your current directory, do
```
 wrestool -x --output=. -t14 ~/.wine/drive_c/Program\ Files/MSN\ Messenger/msnmsgr.exe
```
or something similar

Thanks guys, both of these worked great!

---

### Post by Chris Weaver on 2009-03-18
This is just what I need. Using WINE apps under the menu is OK with that weird spring "Launcher" icon but it's good to have old you are familiar with.

Coincidently, the output of 

```
wrestool -x --output=. -t14 ~/.wine/drive_c/Program\ Files/MSN\ Messenger/msnmsgr.exe
```

...leaves you with a .ico file which you will then have to convert to a SVG (vector based format) to use in Ubuntu's menu

I went a slightly different route by using [http://wineicons.sourceforge.net/]("http://wineicons.sourceforge.net/") to extract the icon from the exe as a PNG 

Bear in mind that the "Change Icon" dialog will not show the icons in the directory that you navigate to. Click OK and then the dialog will ask you to select from the compatible files it find in the directory (confused me for about an hour!)

---

