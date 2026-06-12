---
title: "libffi4 is missing final newline"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by waraas on 2009-08-07
Hello Everyone,

I am new to ubuntu, but I get the basics of it. I need some help installing the new updates.

Version I am running: Ubuntu 8.04.3 LTS 

My problem is that when I try to upgrade it wont let me because of the error below:

E: /var/cache/apt/archives/language-pack-en_1%3a8.04+20090402_all.deb: files list file for package `libffi4' is missing final newline

So I logged into root and deleted the file. I checked and the file was deleted, I then rebooted and then tried to reinstall the new updates, and I got the same error message as above.

I deleted the file using "rm -i  /var/cache/apt/archives/language-pack-en_1%3a8.04+20090402_all.deb".

I am stuck now on what to do. I tried deleting the file and that didnt work, what other options do I have? And why would I be having this problem in the first place? Is it a bug? This has been the only problem I have had in like 2 years of using ubuntu. I have 55 updates that are pending and I would like to get them installed haha

Thanks in advance for the help :)

---

### Post by Partyboi2 on 2009-08-07
Hi, open a terminal and
```
echo -en '\n' | sudo tee -a language-pack-en.list
```
then
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by waraas on 2009-08-07
> **Partyboi2 said:**
> Hi, open a terminal and
```
echo -en '\n' | sudo tee -a language-pack-en.list
```then
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```


Hello, Thank you so much for the help. I did what you told and the below is what I got on my end.

[PHP]Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/language-pack-en_1%3a8.04+20090402_all.deb (--unpack):
 files list file for package `libffi4' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-en_1%3a8.04+20090402_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/PHP]

---

### Post by Partyboi2 on 2009-08-07
Sorry, my mistake I gave the wrong name in the above command it was meant to be
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libffi4.list 
```

---

### Post by waraas on 2009-08-07
> **Partyboi2 said:**
> Sorry, my mistake I gave the wrong name in the above command it was meant to be
```
 echo -en '\n' | sudo tee -a libffi4.list
```

Hello,

I did the line you mentioned here along with the others. I think it posted the same error, which is below :-s

[PHP]Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/language-pack-en_1%3a8.04+20090402_all.deb (--unpack):
 files list file for package `libffi4' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-en_1%3a8.04+20090402_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/PHP]

Thanks for the help, I have been working on this for 4 plus hours now haha.

---

### Post by Partyboi2 on 2009-08-07
My brain is in sleep mode open a terminal and do[FONT=monospace]
[/FONT]```
 echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libffi4.list
```

Edit: I think my bed is calling for me lol

---

### Post by waraas on 2009-08-07
> **Partyboi2 said:**
> My brain is in sleep mode open a terminal and do[FONT=monospace]
[/FONT]```
 echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libffi4.list
```Edit: I think my bed is calling for me lol


Oh I see I should have caught that :-s Anyways I entered that and I got the same error but with a diff file. Which is 'cpp-4.2' now :-s

[PHP]Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/language-pack-en_1%3a8.04+20090402_all.deb (--unpack):
 files list file for package `cpp-4.2' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-en_1%3a8.04+20090402_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/PHP]

---

### Post by Partyboi2 on 2009-08-07
Do the same for [COLOR=#000000][COLOR=#0000bb]cpp-4.2[/COLOR][/COLOR]
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/cpp-4.2.list
```

---

### Post by waraas on 2009-08-07
> **Partyboi2 said:**
> Do the same for [COLOR=#000000][COLOR=#0000bb]cpp-4.2[/COLOR][/COLOR]
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/cpp-4.2.list
```

Edit, Ops forget about that last part I entered it wrong somehow. haha. I entered the above and now it is saying the same thing for 'cupsys', shall I keep doing the same thing until its fixed?

---

### Post by waraas on 2009-08-08
Hello,

I am sorry to double post but now I am stuck. I entered the same line as above, but I got the same error.

```
(Reading database ... dpkg: error processing /var/cache/apt/archives/language-pack-en_1%3a8.04+20090402_all.deb (--unpack):
 files list file for package `cupsys' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-en_1%3a8.04+20090402_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is what I entered:

```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/cupsys.list
```

I dont know what to do now, I have done and researched the best I could on this problem. :-s

---

### Post by Partyboi2 on 2009-08-08
Your cupsys.list file is empty so try this
```
sudo mv /var/lib/dpkg/info/cupsys.list  /var/lib/dpkg/info/cupsys.list.old
```
```
sudo apt-get --reinstall install cupsys
```

---

### Post by waraas on 2009-08-08
Hello,

thank you again for the help. I have entered that and below is what I got:

```
(Reading database ... 
dpkg: serious warning: files list file for package `cupsys' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/cupsys_1.3.7-1ubuntu3.5_i386.deb (--unpack):
 files list file for package `libgomp1' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/cupsys_1.3.7-1ubuntu3.5_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Also, what is this "missing newline" error mean?

---

### Post by Partyboi2 on 2009-08-08
It seems that your info list is all messed up, I am not sure if there is a way to fix it all up at once, or whether you will continue to have to add the newline to each one manually 
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libgomp1.list
```The newline is a end of line (eol) or a line break. So the error is telling you its missing a line break for that file.

---

### Post by waraas on 2009-08-08
Ok, shall I just reinstall ubuntu then?

---

### Post by Partyboi2 on 2009-08-08
If it was me I would keep working through adding the newline for awhile and hope that it comes right.

---

### Post by waraas on 2009-08-08
Hello,

Its a good thing you said that haha. I entered that last line and then it worked, the system installed all of the updates. I wanted to thank you for helping me out :)

```
jon@jon-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.3 LTS
Release:    8.04
Codename:    hardy

```

Thanks again you helped me a ton! Now I need to find out how to set this to solved hehe.

---

### Post by Partyboi2 on 2009-08-08
Good to hear you got it working :)

---

