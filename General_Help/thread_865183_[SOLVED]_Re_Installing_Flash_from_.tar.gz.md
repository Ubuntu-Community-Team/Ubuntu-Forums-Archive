---
title: "[SOLVED] Re: Installing Flash from .tar.gz"
date: 2008-07-20
forum: General Help
---

### Post by Brain_of_J on 2008-07-20
I'm attempting to install Flash Player 9 from the tar file...
(I don't get prompted to update plugins like in the example from the psychocats page)
I'm trying to follow the directions on this page
[linky](http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu)
after navigating to the directory the files have been extracted to, i get this message

my@Leash:~$ cd /home/my/Desktop/install_flash_player_9_linux
my@Leash:~/Desktop/install_flash_player_9_linux$ dir
flashplayer-installer  libflashplayer.so
my@Leash:~/Desktop/install_flash_player_9_linux$ sudo flashplayer-installer
[sudo] password for my: 
sudo: flashplayer-installer: command not found

any ideas why it's not working? (i'm pretty new to Ubuntu so please be patient...thank you.

---

### Post by aysiu on 2008-07-20
> **Brain_of_J said:**
> I'm attempting to install Flash Player 9 from the tar file...
(I don't get prompted to update plugins like in the example from the psychocats page)
I'm trying to follow the directions on this page
[linky](http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu)
after navigating to the directory the files have been extracted to, i get this message

my@Leash:~$ cd /home/my/Desktop/install_flash_player_9_linux
my@Leash:~/Desktop/install_flash_player_9_linux$ dir
flashplayer-installer  libflashplayer.so
my@Leash:~/Desktop/install_flash_player_9_linux$ **sudo flashplayer-installer**
[sudo] password for my: 
sudo: flashplayer-installer: command not found

any ideas why it's not working? (i'm pretty new to Ubuntu so please be patient...thank you. You're missing a ./ in there.

It should be ```
sudo ./flashplayer-installer
``` not ```
sudo flashplayer-installer
``` A little tip: if you ever get command-line instructions, **copy and paste** them instead of retyping. Saves you time. Minimizes errors.

---

### Post by Brain_of_J on 2008-07-20
aysiu:
thank you.
that worked.

however, now i'm getting a different "error".

[I]Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

[/I]
I checked, and that is the path for the mozilla directory and it does exist.
ideas?

---

### Post by aysiu on 2008-07-20
Yeah, it's weird. I don't know why it won't accept /usr/lib/mozilla

Try /usr/lib/firefox

That should work.

---

### Post by Brain_of_J on 2008-07-20
double post
please delete

---

### Post by Brain_of_J on 2008-07-20
that didn't work either...same error

need a screen shot or anything?

---

### Post by steveneddy on 2008-07-20
Flash 10 is available from the repos.

Seems like it would be easier to install it from there.

---

### Post by aysiu on 2008-07-20
> **Brain_of_J said:**
> that didn't work either...same error

need a screen shot or anything?
Yeah, a screenshot would be nice.

Any reason in particular you're installing it from a .tar.gz?

This would seem to me the simplest way to install it:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Brain_of_J on 2008-07-20
ah-ha!
I had originally tried the psychocats link but since I had installed Gnash at one point, the "you need to install a version of Flash Player" button didn't show...I didn't have the option.
I uninstalled Gnash using Synaptic package manager and was then able to follow the psychocats directions.

Thank you for your time.

---

### Post by r0g on 2008-09-10
> **aysiu said:**
> You're missing a ./ in there.

It should be ```
sudo ./flashplayer-installer
``` not ```
sudo flashplayer-installer
``` A little tip: if you ever get command-line instructions, **copy and paste** them instead of retyping. Saves you time. Minimizes errors.

OK, that works but can anyone explain why? This was puzzling the hell out of me, firstly that it wouldn't launch a script from me typing it's name, and secondly that autocomplete couldn't see the file either.

I'm sure I've run plenty of other things by just typing their names and not had to prefix them with "./", why is that necessary in this case???

Seems pretty weird to me :-/

Roger.

---

### Post by jagrav on 2008-09-19
> **r0g said:**
> OK, that works but can anyone explain why? This was puzzling the hell out of me, firstly that it wouldn't launch a script from me typing it's name, and secondly that autocomplete couldn't see the file either.

I'm sure I've run plenty of other things by just typing their names and not had to prefix them with "./", why is that necessary in this case???

Seems pretty weird to me :-/

Roger.
rOg,
The script will be launched/autocompleted-on-tab provided the directory/folder containing it is in the current path. Type 'echo $PATH' to see your current path.
Suppose you are in some directory that is not in the current path and if you want to launch a script there you will have to specify the script with its path. So when you invoke the script as './flashplayer-installer' you are saying 'the flashplayer-installer script in this directory( the "./")'. Not weird at all, :)

---

