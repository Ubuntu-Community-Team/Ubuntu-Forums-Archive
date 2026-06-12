---
title: "I cant Install Nvidia Geforce7400 (9.10)"
date: 2010-04-02
forum: Hardware
---

### Post by Graywolf0 on 2010-04-02
When i try to activate the nvidia driver from **Hardware drivers **or when i try to open **Synaptic Package Manager **it shows me this message :

                                                            *_'E:Type 'gpg' is not known on line 55 in source list /etc/apt/sources.list, E:The list of sources could not be read.'_*
 

What should i do ?

Thanks in Advance

---

### Post by NightwishFan on 2010-04-02
Open a terminal and run:
```
sudo aptitude update
```

Then open the driver manager and try again. If that does not work, reboot and try again. If that does work, I will help you further.

---

### Post by Graywolf0 on 2010-04-02
I tried it , it didnt work it showed me this message > E: Type 'gpg' is not known on line 55 in source list /etc/apt/sources.list
E: Type 'gpg' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Type 'gpg' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Type 'gpg' is not known on line 55 in source list /etc/apt/sources.list
E: Couldn't read list of package sources  , Reboot then tried it again and still it didnt work .

---

### Post by NightwishFan on 2010-04-02
Ok, go into System -> Administration -> Software Sources.

Check the first four boxes (if they are not already). Below it says 'Download From' choose 'Main Server'. In the second tab, called 'Other Software' uncheck everything. Then hit Close at the bottom. If any error messages show up report them here.

We might have to manually fix the sources.list file.

---

### Post by Graywolf0 on 2010-04-02
i did what you said and it showed me this message 
[B]The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.[/B]

then i pressed on **Reload  **and it showed me this message

[B]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/B]

Then when i pressed close to the message above it showed me this error

[B]E: Type 'gpg' is not known on line 55 in source list /etc/apt/sources.list
E: Unable to lock the list directory[/B]

i again pressed close to the message above it showed me this error 

[B]E: Type 'gpg' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/B]

So what should i do now , Sorry if this is taking your time but i really need to activate the Nvidia driver because everytime i open a video in full screen it starts lagging and then shutsdown

---

### Post by NightwishFan on 2010-04-02
Run this command in the terminal.
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
```

Then do this again:
```
Ok, go into System -> Administration -> Software Sources.

Check the first four boxes (if they are not already). Below it says 'Download From' choose 'Main Server'. In the second tab, called 'Other Software' uncheck everything. Then hit Close at the bottom. If any error messages show up report them here.

We might have to manually fix the sources.list file. 
```

If you do not receive error messages, then try enabling the nvidia driver. If you do, then, run this command:
```
sudo mv /etc/apt/sources.list.backup /etc/apt/sources.list
```

If it gets to that point I can help you further. I know how to do this in Debian, but not Ubuntu.

---

### Post by Graywolf0 on 2010-04-03
I did what you told me and it worked . Thank you

---

### Post by NightwishFan on 2010-04-03
No problem, I am glad you got it working.

---

