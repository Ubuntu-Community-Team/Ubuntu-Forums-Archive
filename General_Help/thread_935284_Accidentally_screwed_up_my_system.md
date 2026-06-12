---
title: "Accidentally screwed up my system :/"
date: 2008-10-01
forum: General Help
---

### Post by Serrya on 2008-10-01
Hello

I was trying to fix something (via terminals) and the intructions i was following online told me to "sudo chown -R <username> /var/www.". So I wrote exactly what I saw (I thought) but then things started to get really weird. 

Now whenever I try to do something in "sudo" it tells me that "sudo must be setuid root" and so i go 

<comp>:~/$ setuid root
it says " setuid is not installed, you can install this by typing "sudo apt-get install super"

which is a sudo function....you get the idea with what kind of hellish circle i get in :/ Can it be fixed?

---

### Post by LowSky on 2008-10-01
First off what were trying to do that got you to this point?

---

### Post by Serrya on 2008-10-01
I was trying to install Wordpress. And it wouldn't work so I found some guides online (How to get apache2, mySQL and PHP) and then when I got to the wordpress part it said to install the files in the "/var" directory and to do that i needed to change the permissions so it told me to type (as close as i can remeber) 

sudo chown -R <username for mySQL>/var/www.

Then screens of text came piling up and since then I keep getting those messages for sudo

---

### Post by Yellow Pasque on 2008-10-01
Boot to recovery console (should be in your boot menu when you start the computer)
```
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
chmod 4755 /bin/su
```

Solution found in the good ol' archives [http://ubuntuforums.org/showthread.php?t=251358](http://ubuntuforums.org/showthread.php?t=251358)

---

### Post by Serrya on 2008-10-01
how do I get to the "boot"  menu? Is that the menu I get called 
"Recovery Mode"? (when you press ESC before the Ubuntu screen comes up) there I went to "root (drop root shell prompt)" since it was the only thing that game me command line.

When i typed in any of the commands it just gave me a blank line:
ei: root@Foltan:~# 

So I let it run too the Ubuntu log in screen.

If I try to login it it says : 
"User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. USer's $Home directory must be owned by user and not writable by other users." 

Then I press ok and get "Your session has lasted less then 10 seconds. If you have not logged out yourself, this could mean that there is an installation problem, or that you may be out of diskspace (i have 98 gigs free). Try logging in with one of the failsafe sessions to see if you can fix this problem"

In details it says:

/etc/gdm/Xsession: Beginning session setup...
Can't save user-dirs.dirs
Setting IM through im-switch for locale=en_CA
Start IM through /etc/X11/xinput.d/all_ALL linked to /etc/X11/xinput.d/default
Could not create gnome acceleratores directory /home/<name>/.gnome2/accels':Permission denied

So I press ok and the computer restarts.

SO when it gets back the Ubuntu login i go "options" (at the bottom corner of my screen) Pick Failsafe Terminal which brings me to a terminal screen.

and when i try to put in your instructions . . .

it says:

(for the root:root one)
chown:changing ownership of "/usr/bin/sudo'": Operation not permitted

---

### Post by euopun on 2008-11-22
Hi there,
I had this same problem and found a way to fix it thanks alot to Temüjins help:
[LIST=1]
[*]escape while booting
[*]e
[*]kernal
[*]e
[*]add 2 end "rw init=/bin/bash"
[*]enter
[*]b
[*]Chown root:root /usr/bin/sudo
[*]Chmod 4755 /usr/bin/sudo
[*]Chmod 4755 /bin/su
[/LIST]
This option isnt in all distributions of linux's boot menu(ones like myne lol)

---

### Post by brandonros on 2009-02-20
I had the exact same problem at our school and just deleted my domain directory (/home/DOMAIN) and then remade it and it solved the problems by remaking each users accounts on the individual pc's having problems.

---

