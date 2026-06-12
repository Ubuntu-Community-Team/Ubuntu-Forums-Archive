---
title: "Problem with cannon printer and 9.10..."
date: 2009-11-03
forum: Hardware
---

### Post by collinge on 2009-11-03
I have a cannon pixima 2600 -- i have been having a lot of issues with getting driver to install.  This is what i get so far

```
collinge@Linux:~$ sudo dpkg -i cnijfilter-common_2.90-1_i386.deb
Selecting previously deselected package cnijfilter-common.
(Reading database ... 123854 files and directories currently installed.)
Unpacking cnijfilter-common (from cnijfilter-common_2.90-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cnijfilter-common:
 cnijfilter-common depends on libcupsys2 (>= 1.2.1); however:
  Package libcupsys2 is not installed.
dpkg: error processing cnijfilter-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common
collinge@Linux:~$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cnijfilter-common: Depends: libcupsys2 (>= 1.2.1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
collinge@Linux:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  cnijfilter-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 131kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 123861 files and directories currently installed.)
Removing cnijfilter-common ...
collinge@Linux:~$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


i have looked at the other posts  regarding my printer... is there something different about 9.10 to why the same instructions don't work .. 

tried this:
[http://ubuntuforums.org/showthread.php?p=5337771](http://ubuntuforums.org/showthread.php?p=5337771)
and this:
[http://ubuntuforums.org/showthread.php?t=1070696&highlight=cannon+ip2600](http://ubuntuforums.org/showthread.php?t=1070696&highlight=cannon+ip2600)
even went here :
[http://localhost:631/printers](http://localhost:631/printers)

... nothing seems to work-- i just get a bad install every time.

Anyone want to try?? I have been hand writing all of my work.... PAIN IN THE ***... 

thanks for reading.

---

### Post by collinge on 2009-11-04
bump

---

### Post by collinge on 2009-11-11
I found the problem... I extracted all of the .deb files and found the file that was calling for libsycup2 - I think that file was updated or changed in 9.10...  I changed it to libscup2 witch is the actual file install but i now i dont know how to recompres the file back to .deb... I dont know how to install the files now...

---

### Post by ikem.krueger on 2012-08-28
> **collinge said:**
> I extracted all of the *.deb files
> **collinge said:**
> I dont know how to recompress the file back to *.deb[COLOR=SandyBrown]
[/COLOR] You could use my scripts _[COLOR=DarkOrange][dpkg-unpack]("http://pastebin.com/WJHnZfKg")[/COLOR]_/_[dpkg-build]("http://pastebin.com/DKY4efyQ")_:

```
dpkg-unpack cnijfilter-common_2.90-1_i386.deb
``````
dpkg-build cnijfilter-common_2.90-1_i386.deb
```

---

