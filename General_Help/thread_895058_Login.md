---
title: "Login"
date: 2008-08-19
forum: General Help
---

### Post by needshelp on 2008-08-19
can someone help?

i've just gone through the installation of ubuntu for the second time, the computer rebooted, and it is prompting me for a login

i put in my username and then hit "enter" which moves the cursor to the next line where it asks for a password - it doesn't allow me to put in a password so i hit "enter" again and it says something like "login incorrect"

what's wrong?

---

### Post by tuxxy on 2008-08-19
Is this at a command prompt, your password may just be hidden, type it out as normal and see if it works.

---

### Post by needshelp on 2008-08-20
i don't know if it's a command prompt - it comes up after the computer is turned on 

also, i don't think its hidden because the cursor doesn't move when it is on the line with "password" - i've tried typing it in already anyway

---

### Post by rossjman1 on 2008-08-20
Is this the graphical login screen or text (command line) login? You're really not giving enough info. If it's the command line login the password feedback (* or a circle) is turned off by default, it is turned on by default in the graphical login screen.

---

### Post by ryansagen on 2008-09-11
I have the same problem. I know for a fact that im at the command line becuase I have been using windows for the past ten years. However, im a newbie at this. How do i get to the graphic login? And at the cmd line it wont let me type my password so all i can do is hit enter

---

### Post by MoxieAndWhimsy on 2008-09-11
The password line won't show any activity on the prompt. This is a security feature to keep onlookers from knowing how many characters are in your password. Try just typing the password you used during install, very carefully; it takes some getting used to the lack of feedback.

If that isn't your cup of tea, you can try finding the graphical login on another "screen" (for lack of a better word) by flipping through them with Ctrl-Alt-F1 through Ctrl-Alt-F12 (or more if your computer has them). It should be one of the later ones, right next to the console you watched during boot.

---

### Post by ryansagen on 2008-09-11
> **MoxieAndWhimsy said:**
> The password line won't show any activity on the prompt. This is a security feature to keep onlookers from knowing how many characters are in your password. Try just typing the password you used during install, very carefully; it takes some getting used to the lack of feedback.

If that isn't your cup of tea, you can try finding the graphical login on another "screen" (for lack of a better word) by flipping through them with Ctrl-Alt-F1 through Ctrl-Alt-F12 (or more if your computer has them). It should be one of the later ones, right next to the console you watched during boot.

I still cannot login in. Im going to try and install for the third time. I've been spending the last hour trying to figure it out. I have gotten no where. How do i get to the graphic version?

---

### Post by kokkus on 2008-09-11
To go from command to graphic mode, type 
sudo /etc/init.d/gdm start

To turn on the graphic mode permanently, type
sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/K70gdm

---

### Post by ryansagen on 2008-09-11
> **kokkus said:**
> To go from command to graphic mode, type 
sudo /etc/init.d/gdm start

To turn on the graphic mode permanently, type
sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/K70gdm

many thanks, im in the middle of my third re-install...... im going to try it out after it is done installing.

---

### Post by kokkus on 2008-09-11
My pleasure, but for the future you should know that there are always many different ways to solv problems in ubuntu nomatter where or what so ever.
You really don't have to reinstall and start it all over again.

---

### Post by ryansagen on 2008-09-11
> **ryansagen said:**
> many thanks, im in the middle of my third re-install...... im going to try it out after it is done installing.

After successfully logining in.... I get to ****@****:~$

note the *'s are my personal info


what do i do next?
 Everything is still at a cmd line style...:confused::confused:

---

### Post by kokkus on 2008-09-11
You’re going to have to use visudo to edit your sudoers file:

    EDITOR=gedit sudo visudo

Now you’re going to change:

    USERNAME ALL=(ALL) ALL

to (or add if you don’t have it)

    USERNAME ALL=(ALL) NOPASSWD: ALL

Replace USERNAME with your own.

---

### Post by ryansagen on 2008-09-11
ok well how do i load the OS? Like i mean to see the desktop and acutally start using my server.

---

### Post by kokkus on 2008-09-11
udo /etc/init.d/gdm start

---

### Post by ryansagen on 2008-09-11
> **kokkus said:**
> udo /etc/init.d/gdm start


Gives me a error: "Command not found"

does it matter that I am using the server edition?

---

### Post by Mickey Joe on 2008-09-11
maybe try checking your login ?

 Hit CTRL+ALT+F4 when the login window appears, when the console asks for username enter your and hit enter, the same with password. if wrong than passwords wrong, if correct.. don`t know..
 + Remember Linux is mutch diffrent than others,.. Check you`r caps lock

 (come back with ctrl+alt+f7)

---

### Post by ryansagen on 2008-09-11
no im logged in. but i cant load the desktop. it sits at ryan@Sagen:~$
i cant do anything other then type in the help cmds which dont help me

---

### Post by Mickey Joe on 2008-09-11
maybe try reloading the x server ? (ctrl+alt+backspace)
or if it doesnt load .. maybe this could be usefull
[http://ubuntuforums.org/showthread.php?t=595351](http://ubuntuforums.org/showthread.php?t=595351)

---

### Post by kokkus on 2008-09-11
aah so that's the problem. I though u say u can't login coz u r in non-graphic mode.
OK so to get this clear. You have logged in with username and password but the desktop doesn't show up?

---

### Post by Mickey Joe on 2008-09-11
yeah, he said like that =D gnome doesnt start

---

### Post by ryansagen on 2008-09-11
at first i couldnt log in. but then thanks to u, i can. but ya i cant see the desktop. Keep in mind this is my first startup on the system. Do I have to be connected to the internet or no?

---

### Post by Mickey Joe on 2008-09-11
i`m not shure, but when i setup my ubuntu it downloaded some backs from the network.. But the package should have all needed futures to login =/

 Amm .. still can try
> wmctrl -k on

---

### Post by Mickey Joe on 2008-09-11
tell you like this..
if nothing happens

 login.. 
 than push (CTRL+ALT+F1)
 enter
 > rm -rf .gnome .gnome2 .gconf .gconfd .metacity This will reset all defaults
 and go back to (CTRL+ALT+F7)
 and your done..

---

### Post by ryansagen on 2008-09-11
it still gives me a error saying command not found. This is really comfusing. Windows is so much more simpleir.. I'm going to try to install a differnet version tomarrow. I have to go tho. Its 2am where i live. Please check back later tomarrow if you dont mind if i need a hand.
many thanks to all

---

### Post by Mickey Joe on 2008-09-11
now its 10:55 :D 

ok send me an email tomorrow when you come.. 
[email]mikijs@c4.lv[/email]

---

### Post by kokkus on 2008-09-11
Well, if this may have happen everytime u try to install the OS, I suppose it's the installation CD you should worry about. 
It seams like something went wrong under the installation since u can't even boot correctly.

---

### Post by Mickey Joe on 2008-09-11
last night i was installing xubuntu on my home pc, when i started to get problems too, but than quickley i understand that i have got alternative install and download the main ..

---

### Post by tarps87 on 2008-09-11
> **ryansagen said:**
> Gives me a error: "Command not found"

does it matter that I am using the server edition?

If you want to use Ubuntu as a desktop as well I suggest using the desktop version, especially if your new to Linux and Ubuntu. The server edition is designed to sit in in a corner some where so probably does not have a GUI although I have not used it so can not say for sure.
You can download the desktop iso from the Ubuntu website, if you have a low spec machine I suggest the alternative cd (this is a text based installer by will install the gnome enviroment) if not just use the live cd.
The internet is only needed for updates and installing other programs from the repository.
Is you do have a working internet connection you can try
```

sudo apt-get install gnome-desktop

```

---

### Post by Trail on 2008-09-11
> **ryansagen said:**
> it still gives me a error saying command not found. This is really comfusing. Windows is so much more simpleir.. I'm going to try to install a differnet version tomarrow. I have to go tho. Its 2am where i live. Please check back later tomarrow if you dont mind if i need a hand.
many thanks to all

Well, if you *do* have a clue on what you are doing, Linux is also simple.

As tarps87 said, you should use the Desktop edition. Ubuntu Server edition does not have a desktop at all by default.

---

### Post by tarps87 on 2008-09-11
Aghhhh I understand stand your signature.

---

