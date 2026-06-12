---
title: "cinelerra"
date: 2008-09-26
forum: General Help
---

### Post by Whisper45 on 2008-09-26
Basically, my problem is:

```
me@me-desktop:~$ sudo  apt-get install cinelerra
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: libguicast (= 1:2.1.0-2svn20080707ubuntu) but it is not going to be installed
             Depends: libmpeg3hv (= 1:2.1.0-2svn20080707ubuntu) but 1:2.1.0-2svn20080208ubuntu1 is to be installed
E: Broken packages

```


My brother is using Granular, and less than 10 minutes ago, he installed it using apt-get.

How can I fix this?
Thanks for your help,
Whisper.

---

### Post by cor2y on 2008-09-26
Forget that old version of cinelerra.
The company that makes it released a new version, version 4 in source and binary archives (recommend the binary version myself).
So far it hasn't crashed once seems stable once more.
The only problem i have run into is no audio playback when previewing a clip (could be a pulse audio thing) but it renders out the file with audio correctly.
[http://www.heroinewarrior.com/cinelerra.php3](http://www.heroinewarrior.com/cinelerra.php3)

If cinelerra 4 refuses to start just delete or rename the .bcast folder (its a hidden folder so enable show hidden folders in nautilus) in your home directory.

---

### Post by Whisper45 on 2008-09-26
I downloaded that, and in the readme it says


Run ./cinelerra from this directory.  That's it.

&use_mirror=garr



How? I exported everything in the folder to a folder on the desktop.

---

### Post by Whisper45 on 2008-09-26
No one can tell me how to do this? I do not know. I suck with terminal commands and such..

---

### Post by cor2y on 2008-09-28
To run cinelerra via the terminal
```

~/cinelerra-4-ubuntu-i686/./cinelerra
```
From nautilus go into the folder (cinelerra-4-ubuntu-i686) and double click cinelerra.
If nothing happens or via the terminal you get an error remember to delete the hidden folder .bcast then try it again.

---

### Post by Whisper45 on 2008-09-30
I do not understand. I type that into terminal and I get command not found. So I delete the .bcast and try again, nothing still happens.

---

### Post by cor2y on 2008-10-02
where is cinelerra extracted to?
You have to point to where the cinlerra directory is extracted to.
In my example it was extracted in my home directory.
which is why ~/cinelerra-4-ubuntu-i686/./cinelerra was used.
If you extracted somewhere else then point to where it is example say i extracted the archive in a directory called "video_editing" then the command would be this
```

~/video_editing/cinelerra-4-ubuntu-i686/./cinelerra
```

---

