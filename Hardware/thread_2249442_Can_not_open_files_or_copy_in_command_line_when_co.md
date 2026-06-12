---
title: "Can not open files or copy in command line when connecting Android device in MTP mode"
date: 2014-10-22
forum: Hardware
---

### Post by Jarno_Suni on 2014-10-22
OS: Ubuntu (Studio) 14.04
This is similar case to my situation: [http://stackoverflow.com/questions/25456592/copy-android-mtp-files-using-linux-terminal-or-python-error-operation-not-suppo](http://stackoverflow.com/questions/25456592/copy-android-mtp-files-using-linux-terminal-or-python-error-operation-not-suppo)

My device's Samsung S5 Mini usbid is 04e8:6860 in MTP mode. I can see listings of files in file manager and copy them there (Thunar, PCManFM), but I can not open files there or copy them in command line. I would like to copy (or preferably rsync) files so that I could automate backup of my files from device.

---

### Post by sudodus on 2014-10-22
If you can see the files listed in Thunar and PCManFM, it should be possible to see them and manage them from the command line. Maybe you have not found the path.

When you see the files listed in Thunar or PCManFM, please run the following commands and post the output in a reply

```
df
```
```
sudo parted -ls
```

***Edit***: Is the android device connected to the same computer as you are using to back it up, or to another computer? I'm asking because of gvfs in the path (in the link you provided).

See [URL="https://en.wikipedia.org/wiki/GVFS"]https://en.wikipedia.org/wiki/GVFS

[/URL]Or is the android device itself playing the role as the other computer?

---

### Post by Jarno_Suni on 2014-10-22
I can see the listings of files in terminal under [COLOR=#000000][FONT=monospace]$XDG_RUNTIME_DIR/gvfs[/FONT][/COLOR]  by using ```
cd
``` and ```
ls
```. ```
ls -l
``` tells I have rw acces to the files. But I can not copy them by ```
cp
``` from there. Please note, that for some reason I can not open the files even in file manager, unless I copy the files to local hard disk first. Thunar tries to open file by passing path starting like [COLOR=#000000][FONT=monospace]$XDG_RUNTIME_DIR/gvfs as an argument[/FONT][/COLOR], whereas PCManFM passes the respective URL beginning with [COLOR=#000000]mtp://[/COLOR]. Both ways fail.

---

### Post by Jarno_Suni on 2014-10-22
> **sudodus said:**
> 
When you see the files listed in Thunar or PCManFM, please run the following commands and post the output in a reply

```
df
```
```
sudo parted -ls
```

***Edit***: Is the android device connected to the same computer as you are using to back it up, or to another computer? I'm asking because of gvfs in the path (in the link you provided).

See [URL="https://en.wikipedia.org/wiki/GVFS"]https://en.wikipedia.org/wiki/GVFS

[/URL]Or is the android device itself playing the role as the other computer?

The Android device is connected directly by USB cable to the Ubuntu computer I try to backup the files to. I am giving the commands and using terminal and the file managers in the Ubuntu device. The commands you mention don't give different output after connecting the device.

---

### Post by sudodus on 2014-10-22
It is mounted as 'network' (virtual filesystem) by the file managers. I have not done this with an android device, but I have done something similar between computers (for example connecting to a Windows computer from Ubuntu).

Try searching the internet for ***connect android ubuntu*** or ***connect android linux***

I found the following link, that might help you [URL="http://ubuntuforums.org/showthread.php?t=2226702"][How-To] Connect an Android device using MTP in Ubuntu 14.04 LTS
[/URL]

---

