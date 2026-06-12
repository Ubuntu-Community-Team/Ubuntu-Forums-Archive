---
title: "Uninstalling a software which get installed in root directory"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by madeel on 2009-01-02
I have installed a software which get installed in root directory. At that time I didn't know that I can not copy/delete files in root directory. Now, I want to uninstall/delete it from there. How can I do that safely?

Thanks,

---

### Post by tommcd on 2009-01-02
What program is it? And how did you install it? If it was installed through apt-get or synaptic then you would just use apt-get or synaptic to remove it.

If it was installed from a "sh program-1.0.run" file, or you compiled it from source code (./configure && make && make install) then you will have to find where it was installed to and delete it's directory and any other files it installed. Many third party programs are installed to /usr/local or /opt with a symlink to a launcher in /usr/bin, and with some config file in /etc. Do this:
```
find / -name program_name
```
where program_name is the name of your software. This should list where the program went. Then you would then have to remove it's directory and files with sudo.

Did the software come with a way to uninstall it? And what program is it?

And welcome to the Ubuntu forums!

---

### Post by madeel on 2009-01-02
It was a bin file. It was set up by default to installed in root directory. During installation, installer asked me to change the installation folder but I let it go. It is only later I learned that I can not write any thing outside home directory.

I have figured out that I should use

 sudo nautilus 

to add or remove any files from there. Synpatic also don't know where the software is. I am unsure whether your command can search files in root directory.

Lastly, I am wondering whether this thoughtless deletion has any effect on system. In windows deleting software may prove to be harmful. Is it also true for Linux?

---

### Post by tommcd on 2009-01-02
> **madeel said:**
> 
It was a bin file. It was set up by default to installed in root directory. During installation, installer asked me to change the installation folder but I let it go.
What program was it? And provide a link to where you got it from. 

> **madeel said:**
> 
 Synpatic also don't know where the software is.

Synaptic will only be able to keep track of .deb installs.
> **madeel said:**
> 
 I am unsure whether your command can search files in root directory.

Change the command to:
```

find / -name "program_name*"

```
Include those quotes. the / means the root directory. The -name option will search for anything that has your program_name in it. The * will include anything that includes your program_name.
> **madeel said:**
> 
Lastly, I am wondering whether this thoughtless deletion has any effect on system. In windows deleting software may prove to be harmful. Is it also true for Linux?
As long as you only remove this programs files, and nothing that belongs to any other parts of your system, it will not cause any problems. Most of the program probably went to a dedicated directory in /usr, /usr/local, or /opt. So, for example, if it went to /usr/local you could remove it with:
```
sudo rm -r /usr/local/program_name
```

---

### Post by madeel on 2009-01-03
It was Maple v11. It was given to me by my class-mate. He told me that he had downloaded it from rapidsahre.

---

### Post by tommcd on 2009-01-04
Have you considered asking your class mate how to uninstall it then?

Since you have not told me exactly how you installed it I can only guess. According to this page:
[http://www.maplesoft.com/support/install/InstallMaple11.html#preinstallLS](http://www.maplesoft.com/support/install/InstallMaple11.html#preinstallLS)
the default install is to your home directory:
> By default, Maple 11 will install to $HOME/maple11, where $HOME is your home directory If that is the case then just open up your home directory and delete it.

But since you said you installed it to root then perhaps you installed it like this:
[http://www.ces.clemson.edu/linux/maple.shtml](http://www.ces.clemson.edu/linux/maple.shtml)
If that is the case then it was installed to /usr/local/maple11. But you said you did not change the default directory when prompted so I can only guess where it went. Try this:
```
sudo find / -name "maple*"
```
and include the quotes in the command. That should output a list of all files with maple in them. Post the output of that command here.

Do you remember exactly what you did when you installed it? And if so can you post that also?

---

### Post by madeel on 2009-01-04
Its was a .bin file. I run it as 

sudo chmod +x *.bin
sudo .\*.bin

Then a graphical installer came up, similar to Windows. During the installation, it asked whether I want to change the location. By default, it was

\root\maple11

I didn't change it at all. I couldn't delete or paste any file there. 
But I figured it out how can I do that. I use the following command: 

sudo nautilus 

I have deleted the folder maple11 located as subfolder in \root. 

I tried it to install it second time, this time I changed the installation folder:

\home\Maple11

Again I can't write or delete any file unless I use sudo nautilus. I have deleted the folder from there as well.

By the way, I was unable to select any subfolder within home folder.  Perhaps, I should install it anywhere. And whenever I need to access it, I can use the command sudo nautilus.  

And yes, your help is greatly appreciated. I have learned few more things about Ubuntu.

---

### Post by madeel on 2009-01-04
Here is another inquiry. 

At the time I installed Ubuntu, I reserved very little space for the root directory. I didn't know that root directory has a directory dedicated to installing software. 

Is there some way that these software may be installed within subfolder of the home direcotry?

---

### Post by tommcd on 2009-01-05
Some programs will run fine from your home directory. I'm not familiar with Maple, but according to the link I gave in my last post from the Maple website:
[http://www.maplesoft.com/support/install/InstallMaple11.html#preinstallLS](http://www.maplesoft.com/support/install/InstallMaple11.html#preinstallLS)
Maple can be run from your home directory and run just fine. 

Most software in linux will install to /usr, /usr/local, or /opt. If you can't run a particular 3rd party program from your home directory, it is good to install it to /usr/local or /opt. That way it will be kept seperate from all your Ubuntu programs which will be in /usr. When you download a 3rd party program it will usually come with a **readme** or **install** file that will tell you how to install it. Or go to the program's website and read up on how to install it.

It is always best to stick to programs in the Ubuntu repositories that you can easily install and uninstall with synaptic or apt-get. If you need something that is not in the Ubuntu repos, go to the program's website to see if they have a .deb version of their software. That way you can install and uninstall it using Ubuntu's package management system. If there is no .deb installer available, then you will need to run a binary .bin or .run installer, or compile the program from source code. See this for more info:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

