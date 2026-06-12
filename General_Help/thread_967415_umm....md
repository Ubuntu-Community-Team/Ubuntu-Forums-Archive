---
title: "umm..."
date: 2008-11-02
forum: General Help
---

### Post by raucous on 2008-11-02
So a few new changes to my machine. 

I just installed 2 more gigs of ram. 

today i updated intrepidly.

Afterwards i installed compizfusion flawlessly (or so i thought). i was simply choosing the pointer graphics i liked then all hell broke loose. the laptop shut down and when it restarts and i type in my password it goes to my desktop for about 2 seconds then restarts. 

over and over and over again.

now its frozen with a pattern on the screen and im waiting for the battery to die.

so. i bet i didnt have the proper graphics cards. 
and i bet im screwed.

as when vista crashed on me after i installed something i didnt have the drivers for, and i lost my hard drive, i bet i just did that again now didnt i?

---

### Post by raucous on 2008-11-02
oh. 
someone please help.

---

### Post by 3rdalbum on 2008-11-02
You can turn off the computer by holding down the power button.

The problem probably came from your "installing Compiz". Compiz is preinstalled, so I think we really need to know what exactly you did in order to know what's gone wrong. And how to fix it. Because if it's just your desktop that's crashing, mate, there's definitely hope.

---

### Post by raucous on 2008-11-02
ok. so i opened the window where all the options are for deciding what sort of effects you want, like the pointer effects and the color scheme and all that, and im trying to think of what i last selected but i can't. so everything i selected seemed innocent enough. so once again i type in my username and password then it becomes a patterns and sends me back to the username.

im stumped. reminds me of the blue wall of death from my vista days.

---

### Post by loomsen on 2008-11-02
> reminds me of the blue wall of death from my vista days

Forget them ;) You're communicating on a way higher level with your hardware now than you've been on Vista. I just posted some thoughts about the [main differences between open and closed src software here](http://ubuntuforums.org/showthread.php?t=966030&page=3)

OK, nuff o dat offtopic flaming.

So, you somehow broke your X-authority or sth else in gnome such that you aren't able to login anymore, right? Plus, you probably have the wrong driver installed, right?

3rdalbum is right, waiting for the battery to die equals killswitching, so killswitch :D

Is it possible you followed some howto or such and typed one sudo to much?

Anyway, as linux grants us login to a runlevel other than GUI, let's try and make use of it.

Reboot your Computer, after your BIOS screen changes and GRUB loads, hit esc to get to the GRUB menu.

Then chose single user or recovery mode (differes between different distros, but it should look sth like:

2.6.27-7 x86_64 foo_bar

2.6.27-7 x86_64 foo_bar single user mode / recovery mode

2.6.27-7 x86_64 foo_bar memtest

Chose the recovery mode, wait till you get a very basic UI to chose from some Options, and then drop yourself to a root shell. There should be such an Option.

First, lets add some users, so that even if you won't be able to log back in, you still won't have to reinstall your OS.
the command to create a new user is
```

me@tiffany:~$ adduser foo 

```

You'll be prompted some questions then, but usually its enough to specify some name and a passwd.

```

root@tiffany:~# adduser foo
Adding user `foo' ...
Adding new group `foo' (1001) ...
Adding new user `foo' (1001) with group `foo' ...
Creating home directory `/home/foo' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for foo
Enter the new value, or press ENTER for the default
	Full Name []: foo_bar
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] y
root@tiffany:~# 

```

Add 2 or 3 users to have a fallback backup.

OK, and then you should find out what graphics card you have, and post it here.

---

### Post by raucous on 2008-11-02
HA! success.

so what i did was upon startup i selected failsafe terminal mode. i went in there and typed:

sudo aptitude -y remove compiz-core desktop-effects
sudo aptitude -y remove compiz compiz-gnome
sudo aptitude -y remove compizconfig-settings-manager
sudo aptitude -y remove compiz-fusion-plugins-extra
sudo aptitude -y remove compiz-fusion-plugins-unofficial
sudo aptitude -y remove libcompizconfig-backend-gconf

then:
sudo reboot


i still got the wierd colored lines that i had never gotten before but at least i made it back to my desktop where everything was just as i left it. 

so whatever i selected in the compizfusion menu did not sit well with my machine and uninstalling it took care of the problem.

anyway im not touching it with a ten foot pole. 


hope this this was helpful to someone. 
[or at least comical]


thanks for the reply 3rdalbum. i hope your enjoying spring. we got our first snowfall today in upstate new york.

---

### Post by raucous on 2008-11-02
thanks loomsen. 
i didnt even get to read your post but im much obliged regardless.
word.

and this is the card. [good thinking]

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by 3rdalbum on 2008-11-02
Well, I'm glad that's sorted. It sounds like some of the settings you chose conflicted with Compiz, although that's something I haven't heard of happening for a long time.

If you go to the top of this post and click "Thread Tools" you can mark your thread as "solved".

---

