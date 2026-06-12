---
title: "Ubuntu 8.10 &quot;No space left on device&quot;"
date: 2009-04-15
forum: Hardware
---

### Post by rickcjmac on 2009-04-15
I tried to install OOoLaTeX with a series of commands through the terminal following the directions from [http://ubuntuforums.org/showthread.php?t=334218](http://ubuntuforums.org/showthread.php?t=334218) 

**Install dependencies:**
Code:

sudo apt-get install texlive imagemagick epstool

**Install Mathematical Fonts:**
Code:

mkdir OOoLatexFonts
cd OOoLatexFonts
wget [http://mesh.dl.sourceforge.net/sourceforge/ooolatex/OOoLatexFonts.zip](http://mesh.dl.sourceforge.net/sourceforge/ooolatex/OOoLatexFonts.zip)
unzip OOoLatexFonts.zip
cd ..
sudo mv OOoLatexFonts /usr/share/fonts/truetype/.
sudo fc-cache -f /usr/share/fonts/truetype

The last step may take a while before finishing

I got to 

sudo mv OOoLatexFonts /usr/share/fonts/truetype/.

then I got the message that the file didn't exist. I tried to just make a file as root, but it didn't work, saying "No space left on device." 
I get that same message everytime I try to save or copy and paste anything in any file.

Any help is appreciated. Thanks.

---

### Post by HankB on 2009-04-16
> **rickcjmac said:**
>  "No space left on device." 


Disk full? Can you free up some space and try again?

HTH,
hank

---

### Post by rickcjmac on 2009-04-16
I cleared up a few gigs of mp3 and mp4 files. Same problem still. When I open OpenOffice.org I get the message:

"Either another instance of OpenOffice.org is accessing your personal
settings or your personal settings are locked.
Simultaneous access can lead to inconsistencies in your personal 
settings. Before continuing, you should make sure user "closes
OpenOffice.org on host"."

Do you really want to continue? Yes/No

So I click "Yes" then this pops up:

"OpenOffice.org could not save the important internal informationdue to insufficient free disk space at the following location:
/home/lightning/.openoffice.org2/user/backup

You will not be able to continue working with OpenOffice.org without allocating more free disk space at that location.

Press the 'Retry' button after you have allocated more free disk space 
to try saving the data.

"Retry""

After I hit "Retry" a few times it opens up. I looked for that file and it isn't in that directory. I tried to make a folder with that name in that directory, but the computer told me that I couldn't because there was already a folder with that name in that directory.

When I try to save a document in OpenOffice.org I get the message:

"Error saving the document "whatever":
General Error.
General input/output error."

It is possible that I messed up the directory or something. I really don't know. Again, any help is appreciated. Thanks.

---

### Post by HankB on 2009-04-16
First, post the output of [FONT="Courier New"]df[/FONT] typed in a terminal.

Next, check permissions on all of the directories in the path listed by OO: [FONT="Courier New"]/home/lightning/.openoffice.org2/user/backup[/FONT] 

If you ever ran OO as root, it could have created directories or files that you cannot access due to permissions problems. You can probably fix this by runnning:

[FONT="Courier New"]sudo chown -R <user>.<user> *[/FONT]
(Where you replace <user> with your login ID. The "no space left on device" may just be an error message produced when OO cannot create a file due to permissions problems.

HTH,
hank

---

### Post by rickcjmac on 2009-04-17
lightning@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      13457172   9619936   3153644  76% /
tmpfs                  1551424         0   1551424   0% /lib/init/rw
varrun                 1551424       108   1551316   1% /var/run
varlock                1551424         0   1551424   0% /var/lock
udev                   1551424      2820   1548604   1% /dev
tmpfs                  1551424        12   1551412   1% /dev/shm
/dev/sda1            231946436  96762784 135183652  42% /host
lrm                    1551424      2004   1549420   1% /lib/modules/2.6.27-11-generic/volatile

I can't see the file /home/lightning/.openoffice.org2 It isn't in that location. I don't know where it's at, but it's not there. Thanks.

---

### Post by HankB on 2009-04-17
> **rickcjmac said:**
> ```
lightning@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
**                      13457172   9619936   3153644  76% /**
tmpfs                  1551424         0   1551424   0% /lib/init/rw
varrun                 1551424       108   1551316   1% /var/run
varlock                1551424         0   1551424   0% /var/lock
udev                   1551424      2820   1548604   1% /dev
tmpfs                  1551424        12   1551412   1% /dev/shm
/dev/sda1            231946436  96762784 135183652  42% /host
lrm                    1551424      2004   1549420   1% /lib/modules/2.6.27-11-generic/volatile
```

It appears that there space available. That means the "no space" error message results from some other problem creating the file. (I have to admit that I don't recognize the pattern of /host on the physical partition and / mounted below that. I'm presuming that is the result of some sort of disk management and not some indication of a problem.)

> 
I can't see the file /home/lightning/.openoffice.org2 It isn't in that location. I don't know where it's at, but it's not there. Thanks.

What happens if you try to create that directory manually?

-hank

---

### Post by rickcjmac on 2009-04-17
> What happens if you try to create that directory manually?


When I tried to create a folder with the name ".openoffice.org2" an error message came up:

The item could not be renamed.
The name ".openoffice.org2" is already used in this folder. Please use a different name.

Is it possible that Windows could alter the system, due to my partitioned hard drive? I might have to just uninstall Windows altogether. Not really a problem, because I haven't used it in months.

---

### Post by HankB on 2009-04-17
> **rickcjmac said:**
> When I tried to create a folder with the name ".openoffice.org2" an error message came up:

The item could not be renamed.
The name ".openoffice.org2" is already used in this folder. Please use a different name.

Is it possible that Windows could alter the system, due to my partitioned hard drive? I might have to just uninstall Windows altogether. Not really a problem, because I haven't used it in months.
And previouisly
> I can't see the file /home/lightning/.openoffice.org2 

I'm reading but not understanding. ;)

Linux/Unix tools hide files by starting the name with a period. You can see these files and directories by adding the [FONT="Courier New"]-a[/FONT] option to the [FONT="Courier New"]ls[/FONT] command or going to the view menu in the graphical browser and telling it to show hidden files. Now you can check permissions on those directories ([FONT="Courier New"]ls -la[/FONT])

I cannot imagine windows causing this difficulty unless you used some sort of loadable driver in windows to manipulate your Linux file system. I've run dual boot systems for decades w/out windows causing that sort of problem.

HTH,
hank

---

### Post by rickcjmac on 2009-04-19
> Linux/Unix tools hide files by starting the name with a period. You can see these files and directories by adding the -a option to the ls command or going to the view menu in the graphical browser and telling it to show hidden files. Now you can check permissions on those directories (ls -la)

That worked. I went to /home/lightning then went to view>show hidden files, which showed all of the files starting with a period, including my .openoffice.org2 file. 

I right clicked the file, went to properties, clicked the permissions tab and saw:

> Folder access:     Create and delete files
File access:       ---
Group:             lightning
Folder access:     none
File access:       ---
Others
Folder access:     none
File access:       ---


I changed both Folder access options to:

> Folder access:     Create and delete files
File access:       ---
Group:             lightning
Folder access:     Access files
File access:       ---
Others
Folder access:     Access files
File access:       ---


Now I can pull up openoffice.org with no error messages and I can save files with no problems. 

Thank you Hank:D

---

### Post by HankB on 2009-04-19
> **rickcjmac said:**
> That worked. ... Now I can pull up openoffice.org with no error messages and I can save files with no problems. 

Thank you Hank:D

Glad to help and you're welcome.

---

