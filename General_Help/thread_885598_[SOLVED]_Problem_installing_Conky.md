---
title: "[SOLVED] Problem installing Conky"
date: 2008-08-10
forum: General Help
---

### Post by Beth1957 on 2008-08-10
Running Ubuntu Hardy Heron. 
I tried to download Conky using Synaptic, but got the following error message: 
E: conkygui: subprocess post-installation script returned error exit status 127 
 
I tried to remove, completely remove, and reinstall using Synaptic but kept getting the same error message. 
 
I then tried downloading using apt-get instal (as root) and got the following:- 
 
liz@liz-laptop:~$ sudo apt-get install conky 
[sudo] password for liz:  
Reading package lists... Done 
Building dependency tree  
Reading state information... Done 
conky is already the newest version. 
The following packages were automatically installed and are no longer required: 
gappletviewer-4.2 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
1 not fully installed or removed. 
After this operation, 0B of additional disk space will be used. 
Setting up conkygui (1.2) ... 
/var/lib/dpkg/info/conkygui.postinst: 3: update-menus: not found 
dpkg: error processing conkygui (--configure): 
subprocess post-installation script returned error exit status 127 
Errors were encountered while processing: 
conkygui 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
liz@liz-laptop:~$  
 
I tried to remove gappletviewer-4.2 as suggested but got :- 
 
liz@liz-laptop:~$ sudo apt-get autoremove 
Reading package lists... Done 
Building dependency tree  
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
1 not fully installed or removed. 
After this operation, 0B of additional disk space will be used. 
Setting up conkygui (1.2) ... 
/var/lib/dpkg/info/conkygui.postinst: 3: update-menus: not found 
dpkg: error processing conkygui (--configure): 
subprocess post-installation script returned error exit status 127 
Errors were encountered while processing: 
conkygui 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
 
 
Can anyone help? I'm a newbie so if anyone can provide a solution in words of one syllable I'd appreciate it ;)

---

### Post by Diabolis on 2008-08-10
Conky is already installed. The package that is giving you trouble is Conky GUI. Are you trying to install it with the .deb?

I am developing Conky GUI and I made the package **conkygui_v12_all.deb**, but after discovering that it had a error I removed it from the download page. Use the .jar instead.

The error that **conkygui_v12_all.deb** has is the following:

The post post-installation script and the pre-remove script try to execute the command *"update-menus"*, I made the assumption that all the systems had that command. Of course I was wrong and some systems don't have it.

If you already installed Conky GUI with the .deb, you can remove it easily. You just need to edit 2 files.

Execute this in a terminal:
```
sudo gedit /var/lib/dpkg/info/conkygui.postinst
```

delete the line that says "update-menus"

```

sudo gedit /var/lib/dpkg/info/conkygui.prerm
```

delete the line that says "update-menus"

now you can just:
```

sudo apt-get remove conkygui
```

---

### Post by Beth1957 on 2008-08-10
> **Diabolis said:**
> 
 <snip>

Execute this in a terminal:

<snip>

Thank you for the explanation, which I understood :), and for the instructions, which worked beautifully!

I've now downloaded the .tar.gz file. Could you tell me where I should extract it (and the .jar file, of course) to?
TIA

---

### Post by Diabolis on 2008-08-10
Place it wherever you want, it doesn't need installation. You can run the program just by executing the .jar.

You can read more about executing the .jar in [the web site]("http://conkygui.sourceforge.net/")

---

### Post by Beth1957 on 2008-08-10
Thank you very much, you're a :KS
Looking forward to playing with it tomorrow :mad:

---

