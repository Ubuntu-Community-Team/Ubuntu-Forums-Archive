---
title: "[SOLVED] home folder files on desktop"
date: 2008-08-05
forum: General Help
---

### Post by SpikeyMike on 2008-08-05
hi, I noticed that the desktop folder in my home folder had been moved into another folder so I moved it back again, I think I had moved it by accident, I had to use nautilus to do this as it said I didn't have the necessary permissions to move it, the thing is now all the folders in the home folder also appear on my desktop and if I delete them they also get deleted from the home folder, not sure what I have done, anyone any idea?

Spikey

---

### Post by DagMan on 2008-08-06
Not sure if this will solve it.  Either open the configuration editor or type at the terminal
gconf-editor
and navigate to 
/apps/nautilus/preferences
and make sure the box is unticked next to
desktop_is_home_dir

---

### Post by SpikeyMike on 2008-08-06
> **DagMan said:**
> Not sure if this will solve it.  Either open the configuration editor or type at the terminal
gconf-editor
and navigate to 
/apps/nautilus/preferences
and make sure the box is unticked next to
desktop_is_home_dir

hi, thanks for your reply, I checked that but the box isn't ticked, I am sure I have somehow inadvertently created a link between the desktop and home folder when I was using nautilus but not sure how I did it :(

---

### Post by Felonious Punk on 2008-08-06
Try this from the terminal, in your home directory:

```
ls -l
```

If you have created a link to Desktop from your home directory, it will show up there like this:

```
lrwxrwxrwx  1 stuart stuart       25 2008-07-14 17:13 Desktop -> /home/stuart
```

If it's not a link, it will look like this:

```
drwxr-xr-x  4 stuart stuart     4096 2008-08-04 16:26 Desktop
```

Paste the relevant section of the output into a reply.
This may help to determine the problem.

---

### Post by SpikeyMike on 2008-08-07
> **Felonious Punk said:**
> Try this from the terminal, in your home directory:

```
ls -l
```

If you have created a link to Desktop from your home directory, it will show up there like this:

```
lrwxrwxrwx  1 stuart stuart       25 2008-07-14 17:13 Desktop -> /home/stuart
```

If it's not a link, it will look like this:

```
drwxr-xr-x  4 stuart stuart     4096 2008-08-04 16:26 Desktop
```

Paste the relevant section of the output into a reply.
This may help to determine the problem.

Hi, thanks for your reply, I tried that and here is the output, I cannot see any entry for a link between the desktop and home folder, any ideas?

Spikey


[COLOR="Red"]mikey@Ubuntu:~$ ls -l
total 111320
drwxr-xr-x 3 mikey mikey      4096 2008-08-05 14:03 05
-rw-r--r-- 1 mikey mikey     76800 2008-07-16 18:42 7968.doc
-rw-r--r-- 1 mikey mikey      6812 2008-07-14 00:17 acc-1407.gz
drwxr-xr-x 3 mikey mikey      4096 2008-08-06 12:04 amsn_chat
-rw-r--r-- 1 mikey mikey      8743 2008-06-10 11:37 amsn error
drwx------ 2 mikey mikey      4096 2008-08-06 12:05 amsn_received
-rw-r--r-- 1 mikey mikey     10851 2008-07-12 12:33 BBC2.php
-rw-r--r-- 1 mikey mikey   3721216 2008-05-26 21:35 cd080526.iso
-rw-r--r-- 1 mikey mikey     98816 2008-07-07 10:12 customer support engineer motivation.doc
-rw-r--r-- 1 mikey mikey    129536 2008-07-07 09:51 Customer Support Engineer - website.doc
drwxr-xr-x 2 mikey mikey      4096 2008-08-05 13:59 database exports
drwxr-xr-x 2 mikey mikey      4096 2008-08-05 13:59 Documents
drwxr-xr-x 3 mikey mikey      4096 2008-08-05 13:59 downloads
drwxr-xr-x 2 mikey mikey      4096 2008-08-05 18:17 EenvoudPC
lrwxrwxrwx 1 mikey mikey        26 2008-08-05 17:55 Examples -> /usr/share/example-content
-rw-r--r-- 1 mikey mikey        55 2008-07-31 01:17 install codecs
-rw-r--r-- 1 mikey mikey         0 2008-07-31 01:17 install codecs~
-rwxr-xr-x 1 mikey mikey      9886 2008-07-29 14:34 install_vmware.sh
-rw-r--r-- 1 mikey mikey         0 2008-07-29 14:33 install_vmware.sh~
-rw-r--r-- 1 mikey mikey        17 2008-07-07 21:13 joomla_pass
-rw-r--r-- 1 mikey mikey         0 2008-07-07 21:13 joomla_pass~
-rw-r--r-- 1 root  root     386520 2008-07-15 12:50 mail.log
-rw-r--r-- 1 mikey mikey   1839104 2008-02-21 16:54 memtest86+-2.01.iso
drwxr-xr-x 3 mikey mikey      4096 2008-08-05 17:53 michaelsouthern
drwxr-xr-x 2 mikey mikey      4096 2008-08-05 14:03 mobile phonebook backup
-rw-r--r-- 1 mikey mikey     99328 2008-07-07 10:20 motivation.doc
-rw-r--r-- 1 mikey mikey        21 2008-07-06 17:43 mysql_pass
-rw-r--r-- 1 mikey mikey         0 2008-06-11 20:15 mysql_pass~
-rw-r--r-- 1 mikey mikey      3235 2008-07-07 23:03 new file 2
drwx------ 2 mikey mikey      4096 2008-08-05 14:03 PDF
drwxr-xr-x 2 mikey mikey      4096 2008-08-05 14:02 Photos
drwxr-xr-x 3 mikey mikey      4096 2008-08-05 14:03 Pictures
drwxr-xr-x 3 mikey mikey      4096 2008-08-05 14:03 Public
drwxrwxrwx 8 mikey mikey      4096 2008-08-05 14:03 public_html
-rw-r--r-- 1 mikey mikey    353840 2008-08-06 17:50 RealPlayer11GOLD.exe
drwxrwxrwx 4 mikey mikey      4096 2008-08-05 14:03 sites
drwxr-xr-x 2 mikey mikey      4096 2008-06-10 03:25 Templates
drwxr-xr-x 2 mikey mikey      4096 2008-06-10 03:25 Videos
drwxr-xr-x 2 mikey mikey      4096 2008-07-29 15:05 vmware
-rw-r--r-- 1 mikey mikey 106985820 2008-07-26 21:11 VMware-server-1.0.6-91891.tar.gz
drwxr-xr-x 3 mikey mikey      4096 2008-07-11 19:59 webpages
[/COLOR]

---

### Post by SpikeyMike on 2008-08-10
*bump*

---

### Post by Elfy on 2008-08-10
Did you delete Desktop - because it's not there that I can see. 

Run this command and make sure that Desktop is in the line XDG_DESKTOP_DIR="$HOME/Desktop"

 ```
cat ~/.config//user-dirs.dirs
```

If that is ok and > /apps/nautilus/preferences and on the right pane, set desktop_is_home_dir to false is set right in gconf-editor.

Try to make a Desktop folder in your /home and login again.

```
mkdir Desktop
```

---

### Post by SpikeyMike on 2008-08-10
> **forestpixie said:**
> Did you delete Desktop - because it's not there that I can see. 

Run this command and make sure that Desktop is in the line XDG_DESKTOP_DIR="$HOME/Desktop"

 ```
cat ~/.config//user-dirs.dirs
```

If that is ok and  is set right in gconf-editor.

Try to make a Desktop folder in your /home and login again.

```
mkdir Desktop
```

hi, thanks for your reply, I have two questions, when I run the command ```
cat ~/.config//user-dirs.dirs
``` desktop is missing from the line, here is the output

[COLOR="Red"]XDG_DESKTOP_DIR="$HOME/"[/COLOR]

how do I edit the line? I cannot edit it in the terminal

Also I dont have nautilus in the applications menu, how can I open it?

Spikey

---

### Post by Elfy on 2008-08-10
Use gedit 

```
gedit ~/.config//user-dirs.dirs
```

You can open nautilus from a terminal 

```
nautilus
```

This is the whole of my file as well

> # This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

---

### Post by dexter.deepak on 2008-08-10
QUOTE=SpikeyMike;5559890]

Also I dont have nautilus in the applications menu, how can I open it?

Spikey[/QUOTE]

i hope you are asking this question to edit /apps/nautilus/preferences.
  you dont need to open nautilus for that, simply try :
```
gconf-editor
``` in a terminal and goto apps > nautilus > pref.

---

### Post by SpikeyMike on 2008-08-10
thanks for your help, I edited ~/.config//user-dirs.dirs, and restarted the pc and the files are gone from the desktop, would like to know how I managed to change the settings in the first place, no idea how it happened

Spikey

---

### Post by Elfy on 2008-08-10
> **SpikeyMike said:**
> thanks for your help, I edited ~/.config//user-dirs.dirs, and restarted the pc and the files are gone from the desktop, would like to know how I managed to change the settings in the first place, no idea how it happened

SpikeyNot completely sure either tbh

---

