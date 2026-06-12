---
title: "startup problem"
date: 2005-11-08
forum: General Help
---

### Post by Specialsauce on 2005-11-08
whenever i bootup and log in it gives me an error and says gnome may not be able to work properly. it also says that adding Marek to etc/hosts may fix the problem, but etc/hosts is a read-only file, so i cant add anything to it, let alone do i even know where i would put my name....... i suppose i could always make a new 'hosts' file that i could add my name to and move to the etc folder but i dont even know where i would edit the file.....

---

### Post by yoyoned on 2005-11-08
/etc/hosts can be written to by root
```
sudo gedit /etc/hosts
```
add your hostname to the end of the line taht looks like this
```
127.0.0.1 localhost.localdomain localhost 
```

---

### Post by Specialsauce on 2005-11-08
'unable to look up marek via gethostbyname()'

wtf?

---

### Post by Specialsauce on 2005-11-08
im sorry to have to bump this thread, but i really need this question answered..... because its happening when i try to install an internet utility, too, and i need the internet......

---

### Post by oskude on 2005-11-08
hi,

if you wait for more help, i(we) need more info
1. who/what gives this "unable to look up marek via gethostbyname()" ? (and if theres more text before/after that, it could be also usefull to know)
2. whats in your /etc/hosts ?
3. can you "ping marek"

my /etc/hosts looks like
```
127.0.0.1   localhost.localdomain   localhost   testlab
...cut some ip6 shit...
```

so "ping testlab" works here

as "yoyoned" said, you need "sudo" to edit that file

cheers
osku[de]

---

### Post by Specialsauce on 2005-11-08
when i 'ping marek' it just says 'unknown host marek'. and i get the same error message every time when i try to use sudo to edit the etc/hosts file. and as far as what my etc/hosts file contains: all it says is '127.0.0.1 localhost'

---

### Post by oskude on 2005-11-08
[QUOTE=Specialsauce]when i 'ping marek' it just says 'unknown host marek'. and i get the same error message every time when i try to use sudo to edit the etc/hosts file. and as far as what my etc/hosts file contains: all it says is '127.0.0.1 localhost'[/QUOTE]
you get an "unknown host marek" if you type "sudo nano /etc/hosts", huh? :confused: 

so cant you make the changes to /etc/hosts to look like '127.0.0.1 localhost marek' ?

ps. "sudo" asks YOUR password, NOT the root password...

---

### Post by Specialsauce on 2005-11-08
[QUOTE=oskude]you get an "unknown host marek" if you type "sudo nano /etc/hosts", huh? :confused: 

so cant you make the changes to /etc/hosts to look like '127.0.0.1 localhost marek' ?

ps. "sudo" asks YOUR password, NOT the root password...[/QUOTE]
nano? what? huh? im so confused. i never typed anything with nano or anything. i get unknown host marek when i type ping marek, and nothing ever asked for my password..... and no, i cant change etc/hosts to say that, or anything else, for that matter because when i try to access it via the sudo command in the terminal, all i get is the error where it says some crap about 'gethostbyname()'.....

---

### Post by oskude on 2005-11-08
sry,

but this seems to be something that i newer had in my 4years of linux...
heres a thread talking about your problem (sudo gethostbyname) and they seem to have a solution...
[http://ubuntuforums.org/showthread.php?t=78324](http://ubuntuforums.org/showthread.php?t=78324)

[QUOTE="Topsiho"]Problem is solved.
This is what I did:

rebooted in recovery mode. Then you are root.
replaced erroneous line in /etc/hosts with

<home network ip-number> Bromo.Brantas Bromo

rebooted computer in the normal mode

et voila: sudo works again
[/QUOTE]
nano = is a texteditor for console 

so boot in recovery mode and edit the /etc/hosts file with
```
nano /etc/hosts
```
and modify the content to look like
```
127.0.0.1 localhost marek
```
and close nano by pressing "ctrl+x" it will then ask if you want to save the changes, press "y" to confirm. reboot and hope it works :)

if it doesnt work, continue your quest in the thread i mentioned

cheers and good luck
osku[de]

---

### Post by Specialsauce on 2005-11-08
okay, just one last thing...... err...... how to boot in recovery mode.....?

---

### Post by oskude on 2005-11-08
you should have an option in GRUB menu (that black and white menu you get when you boot your computer) where you can select "ubuntu recovery mode" or something like that...

i remember having a ubuntu installation where i had to press "esc" to open the boot menu, otherwise it started ubuntu automaticly...

i hope you know BIOS menu, so DONT go in BIOS menu if your BIOS access key is "esc" :)

---

### Post by Specialsauce on 2005-11-08
it gives the same error when i do that too..... this sucks

---

