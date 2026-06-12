---
title: "adobe-flash plugin broken and unable to fix"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by kitchenguy on 2009-11-04
Hello,

I am running Ubuntu 9.10 Netbook remix on an Acer aspire one.  Running an install of adobe flash player direct from the deb package on their website has failed and now I am unable to get into synaptic or use apt-get in terminal.

I have tried :

[LIST]
[*]sudo apt-get install-f
[*]sudo apt-get purge adobe-flashplugin
[*]sudo apt-get autoremove
[*]sudo apt-get autoremove adboe-flashplugin
[*]sudo apt-get remove adobe-flashplugin
[/LIST]
each time you run thiese commands you get something like:

elisa@Zennie:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.


Same output for purge, auto remove, remove etc.

Tried a manual reinstall but now saying I do not have access to run the deb file.

Can anyone help please?

By the way - massive vote of thanks to the people that made the netbook remix distribution happen - astonishingly good os!!):P

---

### Post by mac9416 on 2009-11-04
Howdy there!

You can uninstall adobe-flashplugin, and install the flashplugin-nonfree with these commands:

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Good luck!

---

### Post by kitchenguy on 2009-11-04
Hello Mac9416,

Thank you very much - it worked a treat. All fixed.

Much appreciated!

---

### Post by QIII on 2009-11-04
If you continue to have flash problems, you may want to uninstall swfdec and gnash.

They conflict with flash.

---

### Post by nairarunraj on 2009-11-04
I am facing the following error:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I am also not able to open the synaptics package manager because of this error...

Please help me out

Thanks.

---

### Post by daveandsheripetersen on 2009-11-04
I was having the same problems as you. I did copy and paste the from Mac 9416 and it works fine now.

Dave

---

### Post by jimgeiser on 2009-11-04
> **nairarunraj said:**
> I am facing the following error:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I am also not able to open the synaptics package manager because of this error...

Please help me out

Thanks.
I am having same problem. I have tried everything and it says I have to re install adobe, but I have tried this, tried what was suggested above and it did not work. Is there a way to go into the folder and remove it? I tried that and it says I do not have permission.

---

### Post by c_ogden99 on 2009-11-05
> **mac9416 said:**
> Howdy there!

You can uninstall adobe-flashplugin, and install the flashplugin-nonfree with these commands:

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```Good luck!

Hello, I'm new to the forum and new to liniux, I have got a Acer Aspire Revo which I decided to go with Linux on and Ubuntu. I did all the updates like it said when I installed it, And then like everyone else with the flash problem I have read went to ....... YOUTIBE lol and tried installing flash, Now I have all these problems and It wont let me install any thing I just get the error message about flash. 

Now I dont know how or where to remove the plugins manually like it suggests also thje above code's to put in the terminal, I dont get how it works 

You put it in and press enter I geuss, but then all I get is:

[sudo] password for callum: 

CAllum being my name, I'm sort of stuck hope someone can help lol 

Thanks

Also I get this when I try to install the  flashplugin-nonfree package.

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by mac9416 on 2009-11-05
> I am facing the following error:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I am also not able to open the synaptics package manager because of this error...

Please help me out

Thanks.

Did you try the commands I suggested? If so, what was the output?

> I am having same problem. I have tried everything and it says I have to re install adobe, but I have tried this, tried what was suggested above and it did not work. Is there a way to go into the folder and remove it? I tried that and it says I do not have permission.

Could you post the output of the commands I suggested? You can run 'gksu nautilus' if you want to remove /var/lib/dpkg/info/adobe-flashplugin.prerm using the file browser, but I would recommend using the command I gave instead.

> Hello, I'm new to the forum and new to liniux, I have got a Acer Aspire Revo which I decided to go with Linux on and Ubuntu. I did all the updates like it said when I installed it, And then like everyone else with the flash problem I have read went to ....... YOUTIBE lol and tried installing flash, Now I have all these problems and It wont let me install any thing I just get the error message about flash.

Now I dont know how or where to remove the plugins manually like it suggests also thje above code's to put in the terminal, I dont get how it works

You put it in and press enter I geuss, but then all I get is:

[sudo] password for callum:

CAllum being my name, I'm sort of stuck hope someone can help lol

Thanks

Also I get this when I try to install the flashplugin-nonfree package.

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Welcome to Ubuntu!

When it says "[sudo] password for callum:", type your password and hit Enter. You will not see the password as you type for security reasons, but it is being entered.

You will only be able to install flashplugin-nonfree after you run the first three commands.

Now, y'all keep in mind that flashplugin-nonfree is only for 32-bit Ubuntu. If any of y'all have 64-bit, I will give you the instructions for installing then.

---

### Post by c_ogden99 on 2009-11-05
> **mac9416 said:**
> Did you try the commands I suggested? If so, what was the output?



Could you post the output of the commands I suggested? You can run 'gksu nautilus' if you want to remove /var/lib/dpkg/info/adobe-flashplugin.prerm using the file browser, but I would recommend using the command I gave instead.



Welcome to Ubuntu!

When it says "[sudo] password for callum:", type your password and hit Enter. You will not see the password as you type for security reasons, but it is being entered.

You will only be able to install flashplugin-nonfree after you run the first three commands.

Now, y'all keep in mind that flashplugin-nonfree is only for 32-bit Ubuntu. If any of y'all have 64-bit, I will give you the instructions for installing then.

Thanks a million it's worked, A little bit of help goes a long way. I only have 32-bit so it worked fine 

Thanks for you help mate your a legend, have been pulling my hair out lol 

Callum

---

### Post by mac9416 on 2009-11-05
Haha, thanks. I'm very glad it worked. Enjoy your new OS!

---

### Post by nairarunraj on 2009-11-05
Quote:
 	 	 		 			 				I am facing the following error:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I am also not able to open the synaptics package manager because of this error...

Please help me out

Thanks. 			 		 	 	 
Did you try the commands I suggested? If so, what was the output?





[quote=mac9416;8248812]Did you try the commands I suggested? If so, what was the output?



Could you post the output of the commands I suggested? You can run 'gksu nautilus' if you want to remove /var/lib/dpkg/info/adobe-flashplugin.prerm using the file browser, but I would recommend using the command I gave instead.

i tried tat command earlier...
it says tat "command not found"

in fact when i tried sudo apt -get install install_flash_player_10.deb
 it gave d same error "command not found"

---

### Post by mac9416 on 2009-11-05
Hey, nairarunraj,

Thanks for posting the output. It's very helpful.

Commands like 'apt-get' and 'dpkg-reconfigure' are all one "word" without spaces. Try it that way, and it should work.
Also, to install a .deb file from disk you will need to use the following command (assuming the file is in your home directory)...

```
$ sudo dpkg -i $HOME/install_flash_player_10.deb
```

However, I would recommend running the commands I gave above first.

Good luck!

---

