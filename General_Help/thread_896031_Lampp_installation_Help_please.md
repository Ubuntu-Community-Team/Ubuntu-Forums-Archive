---
title: "Lampp installation Help please"
date: 2008-08-20
forum: General Help
---

### Post by Freakster on 2008-08-20
Hey Guyz, 

I have a quick problem, i have read the security issues in the main security thread regarding sudo and root logins, and i respect the security issues and keeping the ubuntu security platform.

My main problem is.

I just downloaded xampp-linux-1.6.7.tar.gz file located on my main desktop graphical home screen (logged in as a user)

how do i manage to extract that to a /opt folder which is owned by the root account? 

can anyone provide me with the command via the terminal to extract lampp to the /opt folder?

I have managed to enter this command via my terminal "tar xvfz xampp-linux-1.6.7.tar.gz -C /opt"

but it says locale of specific file cannot be found, or i am placing my downloads in the wrong location.

---

### Post by spiderbatdad on 2008-08-20
if you want to compile to a specific directory use the prefix option during ./configure...like: ./configure --prefix=/opt/xampp...etc

why do it this way though? Perhaps debootstrapping would interest you?
[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

Also there are a number of guides for chrooting apache on Ubuntu...though it doesnt make it inherently more secure...just limits access to root shells...there are much simpler, more effective ways of doing the same.

---

### Post by Freakster on 2008-08-20
i have read the link you provided me, what is debootstrapping mean?

abit new to new terms and literacy,

also i didnt quiet get "./configure --prefix=/opt/xampp...etc"

for example i would have to enter in the terminal like this? "tar xvfz xampp-linux-1.6.7.tar.gz /configue -C /opt/tar xvfz xampp-linux-1.6.7.tar.gz

I am confused on the way how to type it. or to get access to that folder.


This is the link telling me how to install it. but it wont work.
"http://www.apachefriends.org/en/xampp-linux.html#377"

---

### Post by spiderbatdad on 2008-08-20
ok. I looked at that link. You are being asked to run a root shell```
sudo -s
```to gain a root shell.
Make sure that you enter the command exactly, observing syntax...it looks like you did. I have not used this method myself. You can simply extract the tar file on your desktop and run configure with the --prefix=opt/xampp

Your method just worked fine for me:
I downloaded the file to my desktop:
```
sudo -s
cd Desktop
tar xvfz xampp-linux-1.6.7.tar.gz -C /opt

```

You understand lamp is in synaptic package manager...or apache2 if you want to install from the repos using standard beginner methods?

---

### Post by Freakster on 2008-08-20
Wow, i actually didnt add the command "cd Desktop" that why i couldnt extract it. Your a life saver man.

also root shell sudo -s i shall remember that.

I Would like to thankyou for your help, you have been great. i wish we could extend our knowledge in the near future, if you or i require help. (ive added +1 Thanks to your tally total of 340) ;)

---

### Post by Dr Small on 2008-08-20
You only needed to have run one command:
```
sudo tar xvfz ~/Desktop/xampp-linux-1.6.7.tar.gz -C /opt
```

---

### Post by spiderbatdad on 2008-08-20
:) Glad to help.
There are two preferred ways to gain a root shell
sudo -i
sudo -s

use just sudo <command> for single commands as superuser.
The difference between sudo -s and sudo -i is the environment. sudo -s gives me a root shell in user space...I am still in /home/username. sudo-i does not give me any working directory...I have to navigate to it. I'm sure there is more to, but that is what I notice most.
So if you did sudo -i and tried to cd Desktop, you would get file not found. You would have to cd /home/username/Desktop.

---

### Post by spiderbatdad on 2008-08-20
> **Dr Small said:**
> You only needed to have run one command:
```
sudo tar xvfz ~/Desktop/xampp-linux-1.6.7.tar.gz -C /opt
```

This is true, but in the spirit of following a tutorial that asks you to become root...sudo for every command is one way, gaining a root shell is another.

---

### Post by Dr Small on 2008-08-20
> **spiderbatdad said:**
> This is true, but in the spirit of following a tutorial that asks you to become root...sudo for every command is one way, gaining a root shell is another.
Alot of Linux based instructions are based on the core of linux functions to get the task completed, instead of writing a guide for each and every distro out there. That would be real time consuming. Not every distro has sudo installed, etc, so they just write down the core fundamentals to get the job completed. 

That doesn't mean you have to follow the guide to the tee, if you can substitute some commands to get the same output.

Dr Small

---

