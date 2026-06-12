---
title: "how do I make this file executable"
date: 2008-11-24
forum: General Help
---

### Post by ozguitarplayer on 2008-11-24
Hi,
I've been reading and following a forum topic on how to Install and Run lm-sensors and all was good up to saving a file mkdev.sh

then I got lost with;
Make the file executable;
chmod 755 mkdev.sh       

where and how do I do this. and then; 

Run mkdev.sh from the current directory;
sudo ./mkdev.sh

where is the current directory

obviously these questions are from a novice however I'm keen to learn....any help appreciated

---

### Post by Altay_H on 2008-11-24
If the mkdev.sh file is in your home folder (/home/your_name/), you can go to Applications > Accessories > Terminal. From there type in the command:
```
chmod 755 mkdev.sh
```
This will modify the permissions of the file, making it executable.

Same idea with the second question. Provided you just opened the terminal, its current directory is your home folder. Open a terminal window and type the command:
```
sudo ./mkdev.sh
```
This will run the file mkdev.sh located in your home folder with super user permissions. Be careful though. Only run it if you're sure it isn't harmful.

Note: You can copy and paste commands into the Terminal window as well, just remember that you need to use Ctrl+Shift+V to paste into the Terminal and Ctrl+Shift+C to copy from the Terminal.

---

### Post by blazemore on 2008-11-24
to make a file executable, use the chmod command:
```
chmod +x mkdev.sh
```

If it moans that you don't have permission, use sudo

---

### Post by mariashaun on 2008-11-24
Some scripts require that the files are set to executable (chmod 755) and this guide will help you.

Telnet

   1. Connect to your web server with your telnet software
   2. Change directory with cd directory
   3. Type chmod 755 * to change mode for all files in that directory. If you only want to change mode for a special type of file your can use chmod 755 *.txt *.dat or chmod 755 filename.ext. 

FTP
In this example we're going to use WS FTP, but you can use any other FTP software that support chmod UNIX.

   1. Connect to your server and upload the file in ASCII mode
   2. Select the file and right click on it
   3. Select Chmod UNIX in the menu
   4. Check the checkboxes as described on the picture below


to see the check boxes picture visit this url

[http://www.xaviermedia.com/documents/chmod755.php](http://www.xaviermedia.com/documents/chmod755.php)

---

### Post by zvacet on 2008-11-24
> where is the current directory

It is directory where you downloaded package.In most cases it is home directory,but if your package is on desktop run this from terminal

```
cd Desktop
```

After that run commands **Altay_H** adviced.

---

### Post by ozguitarplayer on 2008-11-24
thanks for that, it helped

another question if I may..
being unused the functions of Konsole...if I type in something I often get

nigel@Master:~$

Is what I type in after that a predetermined response or does it vary with
the issue at hand...

---

### Post by jakupl on 2008-11-24
> **ozguitarplayer said:**
> thanks for that, it helped

another question if I may..
being unused the functions of Konsole...if I type in something I often get

nigel@Master:~$

Is what I type in after that a predetermined response or does it vary with
the issue at hand...

"nigel" means that you are logged in as nigel, "@Master" means that you are on the computer called Master, ~ is the symbol for your home directory, in other words "~" is the same as "/home/*yourusername*/". $ is a symbol for witch privileges you currently have.

If you try to make yourself super user for a while you can see what happens.

```
sudo -i
```

This will make it look like this "root@Master:~#"

you are now root, the computer is still called Master, you are in the home directory, (beware, this is not your own home dir, but the home directory of root.), and # means that you now have administrator privileges. 

I think this is how it works, correct me if i'm wrong.

EDIT: you should never become super user without reason, please enter in terminal ```
exit
``` when you are done looking. it is possible to seriously mess up the system if you stay super user.

---

### Post by jakupl on 2008-11-24
These might be at some help.

[http://linuxcommand.org/](http://linuxcommand.org/)

[https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands)

---

