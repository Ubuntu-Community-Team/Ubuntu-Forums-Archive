---
title: "Installing Truecrypt 6.2a in Ubuntu 9.10"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by Chris62 on 2009-06-17
Hi,

Can anyone help with this, please? I was trying to install Truecrypt V6.2a into the current version of Ubuntu. As I have not much experience with this sort of thing I followed a method for installing Truecrypt 4.x into Ubuntu 7.10 that I found in an Ubuntu forum thinking that the method would be the same and that only the file names needed changing.

After downloading  'truecrypt-6,2a-ubuntu-x86.tar.gz'which the web site said would contain a .deb file, I typed 'sudo tar xzvf truecrypt-6.2a-ubuntu-x86.tar.gz' and ended up with a file called 'truecrypt-6.2a-setup-ubuntu-x86' instead of a .deb file as per the method.

Apart from the fact that this file seems to have drifted off into cyberspace, what should I do with it to install Truecrypt when I run the 'sudo tar' command again?

Any help would be gratefully received

Chris

---

### Post by Soul-Sing on 2009-06-17
```
sudo sh directory/to/truecrypt-<version>-setup-ubuntu-<architekture>
``` 
watch the - syntax, then your going into a set-up proces.

---

### Post by Chris62 on 2009-06-18
Thanks leoquant,

I have another problem. I get a message saying "can't open truecrypt....."

I am not very experienced with Linux so perhaps I have not understood your code. What does 'sh' do? and where you have 'directory' should I specify a directory where Truecrypt is to go or should I just type the line as you have put it?

Sorry if I seem exceptionally dim!

---

### Post by Soul-Sing on 2009-06-18
I think, but i'am not sure though:
1) put the file on your desktop
2) ```
cd Desktop
```
3) ```
sudo sh truecrypt-<version>-setup-ubuntu-<architekture>
```
will do

sudo is needed in linux, no program can be installed without sudo.
sh is needed to ¨execute¨ the installproces.

---

### Post by Chris62 on 2009-06-18
Hello leoquant, many thanks for your help. Truecrypt is now installed. The problem was that I had expected the file to be extracted onto the desktop but it wasn't and that is why I was getting the error message saying that it didn't exist..

One last question: how do I alter the properties of Truecrypt so that I don't have to give an administrator password every time I want to use it?
It is no hardship to do that but as I am the only person to use the computer it seems a bit pointless to have to enter my password every time

---

### Post by Soul-Sing on 2009-06-18
Hmmm you can add truecrypt to "users-groups"
and add: %truecrypt ALL=(root) NOPASSWD:/usr/bin/truecrypt
to the sudoers folder via ```
sudo visudo
```

But truecrypt can now be used without any (sudo) permission.....
and data can be easily destroyed, is this a wise/good thing to do?

---

### Post by Chris62 on 2009-06-18
Many thanks again leoquant. All is as I want it now. I see you are located in Amsterdam - what a lovely place it is! I was there a couple of years ago. 

Chris

---

### Post by Soul-Sing on 2009-06-18
Good luck and success with ubuntu, (and truecrypt)

---

### Post by mwjones on 2009-10-02
I received the following error trying to use the graphical installer:

```
dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor
```

Instead, just select **Extract .deb Package File**, then:

```
cd /tmp
sudo dpkg -i truecrypt_6.2a-0_i386.deb
```

---

### Post by benab on 2009-11-03
I was able to install Truecrypt 6.3 on Ubuntu 9.10 without any problem. 
It did not prompt for any dependencies. 

I extracted 'truecrypt-6.3-setup-ubuntu-x86' from the 'truecrypt-6.3-ubuntu-x86.tar.gz' file and then executed:
```
sudo ./truecrypt-6.3-setup-ubuntu-x86
```

It prompted me to agree to the agreement and install without any problems.

---

