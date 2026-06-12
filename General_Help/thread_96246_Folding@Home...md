---
title: "Folding@Home.."
date: 2005-11-28
forum: General Help
---

### Post by floyd27 on 2005-11-28
Hi..
I have been folding in windows but I cant seem to get it going in linux..

How do I get it to start on startup?
If I start it up and close the terminal it stops folding? Can I have it work with the terminal closed.?
Can I use the same client as I use in windows..?

This is what I have done..

Dl'ed 5.02 to home folder.
cd to the dir...
chmod +x FAH502-Linux.exe (what does this do exactally?)
./FAH502-Linux.exe

It ran and Dl'ed a WU. The system manager said 100% usage but the F@H part said 0% cpu usage?
When i closed the terminal folding stopped.

thanx for any help...

---

### Post by MrFahrenheit on 2005-11-28
check out this wiki page:
[https://wiki.ubuntu.com/FoldingAtHome](https://wiki.ubuntu.com/FoldingAtHome)

the chmod +x command is used to make a file executable.  For a more detailed description of the chmod command, at the command prompt, type in 'man chmod'.  This will bring up the manual page for the command.

the man command can be used on any command there is to show manual pages for it.

Hope this helped!

---

### Post by floyd27 on 2005-11-28
ok..What scripts am i suppost to save???? Where are they at?
I have a real hard time reading from the WIKI so I usually dont use it..

Will this make it start up everytime i start linux?
It said there should be an easy way to uninstall it for future plans...So how do you uninstall it now? Or pause it?

---

### Post by floyd27 on 2005-11-28
Im ok in linux but can someone simplify this for me please.. I have tried several times and get no where...
What scripts do I have to save? Where are they ?

...................................................................................................

The following script will download the latest client from the Folding@Home website, and install it to /opt/foldingathome. It will ask you to set up the client (the defaults are usually sufficient), and copy that configuration for every CPU in your machine.

It is not possible to provide a .deb package for Folding@Home, because the client must be downloaded from Stanford's website. This is to ensure the integrity of the research.

[COLOR="DarkOrange"]Save these scripts to the same directory[/COLOR], and name them folding_install.sh and foldingathome, respectively. Then do

chmod 500 foldingathome folding_install

to make them executable. Finally, do

sudo ./folding_install.sh

to install the client.

folding_install.sh-10092005 foldingathome-10092005

---

### Post by MrFahrenheit on 2005-11-28
[QUOTE=floyd27]...I have a real hard time reading from the WIKI so I usually dont use it..[/QUOTE]

Ok, lets fix that problem first.

What exactly is wrong with the wiki?  Are you getting errors on the pages?  Fonts all messed up?

---

### Post by floyd27 on 2005-11-28
No. the page is fine..
I just find it hard to understand WIKI instructions... They are too linux for me  :) 
Sometime it assumes you know a bit too much.. if it was say, translated to english that would be great.. Seriously I dont understand what "scripts" it is refering to?
thanx

---

### Post by MrFahrenheit on 2005-11-28
the scripts are on the page near the end before the "Future plans" section

---

### Post by floyd27 on 2005-11-28
ok..
I managed to get this up and running???
Just a few quick questions..

1-windows has a GUI to look at the folding (not the screensaver) does linux have one?
2-Im using the exact username as in windoes is this ok? Will thwe WU's just combine? Do both clients use the same protien or different ones. (if 1 isnt done)
3-In ~top it says F@H is using 100% but in system monitor it says nice 19 and 0% usage but the cpu is at 100%.
4-I had it start up at boot "damon" is there a way to pause this ...
5-How do i uninstall if something goes wrong?

---

### Post by floyd27 on 2005-11-28
Hi again..
I have folding going but i dont know if its worknig or not?
Cpu is at 100% but there is no log file for me to look at.. And i cant see any GUI at all? Is there one? How do you know what you are currently doing?

---

### Post by MrFahrenheit on 2005-11-30
1.  There is no linux gui
2. this is good, I use the same username on a few computers, they work on different protiens but all the points go to the same name.
3. no clue
4. use the command "sudo /etc/init.d/foldingathome stop" to stop the daemon.  You can also use restart and start commands.
5. To uninstall, you need to remove it from init.d.  You use the command update-rc.d to do this (I don't remember exact syntax, check the man page).  This will stop it from starting at boot time.  Then you can just delete the files. (to find them, try 'locate foldingathome').

log files should be in the foldingathome directory.  

you can also check your stats at the folding.stanford.edu site.

---

### Post by floyd27 on 2005-11-30
thank you very much...

---

### Post by nbcthreat on 2005-12-05
For those of you doing folding, you should consider joining Team Ubuntu. The team number is 45399.

Here's a link to the stats

[http://fah-web.stanford.edu/cgi-bin/main.py?qtype=teampage&teamnum=45104](http://fah-web.stanford.edu/cgi-bin/main.py?qtype=teampage&teamnum=45104)

We're already in the top 5%! Come join the team and let's get up there.

---

### Post by Gray. on 2005-12-05
OK this is weird.... I just went to download the Linux client and its a .exe file.

*EDIT* Nevermind. Followed the Ubuntu wiki and it all worked out fine. Although I had to rename the files so that they were recognised by the script.

Anyone else who has troubles installing it should make sure to rename the file so that it is foldingathome. And set Team number as 45399 :D

---

### Post by Robocoastie on 2005-12-05
that howto and script rox! i had been loading my two instances by hand until now. :) 

Question though. Does the Linux console version of FAH throttle down/free cpu cycles when you need it like the windows version does? When I ran it in the past with Xandros it never seemed to free up cycles as easily as the windows version under wine would. (note that was on my single proc Duron 900 I understand that can't be used in smp machines).

---

