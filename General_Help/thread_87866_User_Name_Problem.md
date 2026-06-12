---
title: "User Name Problem"
date: 2005-11-09
forum: General Help
---

### Post by motormouth on 2005-11-09
When i installed ubuntu and created my root user name I made my regular user account the same.  Now when I log in under this name, its always under the account with regular user permissions so I cannot move files around, etc.  Is there any way for me to fix this? :confused:

---

### Post by RAOF on 2005-11-09
You would not have created a root password on install (Ubuntu doesn't - the root password is set to a random string, I believe), and in fact the root username is always "root".  If you want to do something that requires root access, prepend the command with "sudo", so 
```
mv somefile /usr/local/somefile
or
emacs /etc/ssh/sshd_config
```
becomes
```
sudo mv somefile /usr/local/somefile 
or
sudo emacs /etc/ssh/sshd_config
```

This has the advantage over using a regular root account that all the things you do with root are logged, and the disadvantage that it's a little less convenient to do stuff as root.  Which you shouldn't be doing a lot of, anyway ;)

---

### Post by motormouth on 2005-11-09
[QUOTE=RAOF]You would not have created a root password on install (Ubuntu doesn't - the root password is set to a random string, I believe), and in fact the root username is always "root".  If you want to do something that requires root access, prepend the command with "sudo", so 
```
mv somefile /usr/local/somefile
```
becomes
```
sudo mv somefile /usr/local/somefile 
```

This has the advantage over using a regular root account that all the things you do with root are logged, and the disadvantage that it's a little less convenient to do stuff as root.  Which you shouldn't be doing a lot of, anyway ;)[/QUOTE]

I'm afraid i'm a bit lost, I've only started using linux about 24 hours ago :oops: All i'm trying to do is move a file into a folder and I receive a message telling me I don't have permission to do so?

---

### Post by RAOF on 2005-11-09
Ah, ok.  Well, where are you trying to move the file to?  

You will have write permissions to your home directory (/home/yourusername), and not to much else as a regular user.  Basically, your home directory is like a super version of the windows "My Documents" folder - everything that is just for you should go in there, or in some subfolder.

When you want to install something, Ubuntu will ask you for your password in order to gain the necessary root-privileges to install the program.

I would suggest looking at the [Ubuntu Starter's Guide]("http://help.ubuntu.com/starterguide/C/").  That doesn't particularly address the fundamentals of linux use, but it does show how to install programs, audio-video applications, and the like.

---

### Post by motormouth on 2005-11-09
[QUOTE=RAOF]Ah, ok.  Well, where are you trying to move the file to?  

You will have write permissions to your home directory (/home/yourusername), and not to much else as a regular user.  Basically, your home directory is like a super version of the windows "My Documents" folder - everything that is just for you should go in there, or in some subfolder.

When you want to install something, Ubuntu will ask you for your password in order to gain the necessary root-privileges to install the program.

I would suggest looking at the [Ubuntu Starter's Guide]("http://help.ubuntu.com/starterguide/C/").  That doesn't particularly address the fundamentals of linux use, but it does show how to install programs, audio-video applications, and the like.[/QUOTE]

I've installed XMMS as to listen to MP3s and figured i'd learn how to install plugins for it at the same time.  I've read that i can put the plugin i've downloaded into my user/lib/xmms/visualization folder to load it, however I was only able to download the plugin to my desktop, its when i try to move it to this folder that I don't have access.  Thanks for your patience here

---

### Post by nszabolcs on 2005-11-09
[QUOTE=motormouth]I've installed XMMS as to listen to MP3s and figured i'd learn how to install plugins for it at the same time.  I've read that i can put the plugin i've downloaded into my user/lib/xmms/visualization folder to load it ...[/QUOTE]

you can also put your xmms plugins in your home directory under the .xmms/Plugins folder:
/home/yourname/.xmms/Plugins
(well you won't see files begining with . in nautilus by default, but it's there)

in your case you can do:
```

mkdir ~/.xmms/Plugins/Visualization
cp libsomeplugin.so ~/.xmms/Plugins/Visualization

```


for ubuntu i would rather recommend beep-media-player instead of xmms:
[http://www.sosdg.org/~larne/w/BMP_Homepage](http://www.sosdg.org/~larne/w/BMP_Homepage)

it's compatible with xmms (well plugins won't work but lots of xmms plugins already ported), and uses gtk2 (much nicer preferences dialog)

there is a new version of bmp which is still under development, but looks very promising:
[http://bmpx.kicks-ass.net/w/index.php/BMPx_Homepage](http://bmpx.kicks-ass.net/w/index.php/BMPx_Homepage)

---

