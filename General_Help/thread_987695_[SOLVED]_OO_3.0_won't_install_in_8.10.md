---
title: "[SOLVED] OO 3.0 won't install in 8.10"
date: 2008-11-19
forum: General Help
---

### Post by wc4r on 2008-11-19
I'm a real newbie here. 

I want to install OO 3.0. I extracted the file and placed it on my desktop. The file is identifies as 
OOO300_m9_native_packed-1_en-US.9358
I tried different install command lines in terminal but no luck. What should I be doing?

I really wish there was a more common automatic installation routine. I checked into the add/remove programs way but it will install the old version from [www.go-oo.org](www.go-oo.org). I want v3.0

Joe

---

### Post by 73ckn797 on 2008-11-19
> **wc4r said:**
> I'm a real newbie here. 

I want to install OO 3.0. I extracted the file and placed it on my desktop. The file is identifies as 
OOO300_m9_native_packed-1_en-US.9358
I tried different install command lines in terminal but no luck. What should I be doing?

I really wish there was a more common automatic installation routine. I checked into the add/remove programs way but it will install the old version from [www.go-oo.org]("http://www.go-oo.org"). I want v3.0

Joe


Follow this:
I have installed OO 3.0 on my desk and laptops with Intrepid. Everything was effortless and is running great.

I completely removed all OO related installs through Synaptic.

Downloaded the file (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) from Openoffice.org

Created a directory in /home/name/whatever. (whatever you want to name it)

Extracted files using File Roller (default Gnome compression utility) to the created directory. 

Went to terminal and "cd" to new directory (example: /home/name/OO3/DEBS) then entered "sudo dpkg -i *.deb" The "DEBS" sub-directory is created when extracting. This installs the program.

Then changed to the other sub-directory created during extract (~/DEBS/desktop-integration) and repeated command "sudo dpkg -i *.deb". This creates the menu choices.

Started OO 3.0 and it works like a charm for me.

The desktop icon created using menu right click was read only but right click, properties allows changing that so I could rename the shortcut icon.

OR:
follow suggestions in this thread: [http://ubuntuforums.org/showthread.php?t=968185](http://ubuntuforums.org/showthread.php?t=968185)

---

### Post by fooman on 2008-11-19
no need to uninstall the old version...just add the launchpad openoffice repositories to apt's sources.list and update.

first open a terminal and type or copy/paste the following:

```
gksudo gedit /etc/apt/sources.list
```

when it opens, add (copy/paste) the following lines to the bottom of the file:


```
##repo for open office3
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

save, then close the file and run these 2 commands one at a time:

```

sudo apt-get update
sudo apt-get dist-upgrade
```

thats it...open office 3 should be installed and in the menu: applications > office

or just start it up from the terminal:

```
openoffice
```

---

### Post by wc4r on 2008-11-20
I tried your routine fooman since it was more straight forward. It downloaded and installed fine. Then I went to run it and there was nothing in Application>office. I tried it from terminal and got this:

joe@joe-linux:~$ openoffice
/usr/lib/openoffice/program/soffice: 237: /usr/lib/openoffice/program/../basis-link/program/pagein: not found
/usr/lib/openoffice/program/soffice: 254: /usr/lib/openoffice/program/soffice.bin: not found
joe@joe-linux:~$ 

Thanks!
Joe

---

### Post by wc4r on 2008-11-21
I got it working. Took a different route, easier actually. Used synaptic package manager. Looked almost windows like.

---

### Post by 73ckn797 on 2008-11-21
> **wc4r said:**
> I got it working. Took a different route, easier actually. Used synaptic package manager. Looked almost windows like.


Go to Thread Tools and mark thread as solved with any more info you can provide as to the solution. Details can help the next person more quickly resolve their issues. It is the Ubuntu way.

---

### Post by anhvu2875 on 2008-11-28
> **fooman said:**
> no need to uninstall the old version...just add the launchpad openoffice repositories to apt's sources.list and update.

first open a terminal and type or copy/paste the following:

```
gksudo gedit /etc/apt/sources.list
```

when it opens, add (copy/paste) the following lines to the bottom of the file:


```
##repo for open office3
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

save, then close the file and run these 2 commands one at a time:

```

sudo apt-get update
sudo apt-get dist-upgrade
```

thats it...open office 3 should be installed and in the menu: applications > office

or just start it up from the terminal:

```
openoffice
```

i followed this but nothing to upgrade !! :confused::confused::(

```
Reading package lists... Done
anhvu2875@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Skripka on 2008-11-28
> **anhvu2875 said:**
> i followed this but nothing to upgrade !! :confused::confused::(

```
Reading package lists... Done
anhvu2875@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The packages in the OOo3 PPA have been pulled temporarily due to a bug involving Gnome.

---

### Post by Bert Mariën on 2008-11-28
Also noticed that, and I just installed Ibex anew. Grrr.
Well... I (we) 'll have to wait till it's fixed.
Hope it'll be fixed soon though.

---

