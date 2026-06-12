---
title: "AVG8.5 antivirus issue"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by ranjith.ts on 2009-06-23
Hi people,,

since i came from windows background...just to be on the safer side i wanted to install avg anitivrus

i downloaded the latest avg85flx-r287-a2632.i386.deb file and ran the package and it said installation complete

but i don see that icon anywhere under applications... i am confused

ANy help is much appreciated

---

### Post by wpshooter on 2009-06-23
Probably has to be ran from the terminal.  Look to see if there was a readme file that gives instructions on how to run.

But, IMO, running this on Ubuntu, is likely a waste of recources.

---

### Post by ranjith.ts on 2009-06-23
hi guys

i followed this link:

tried option 1

i Opened a terminal (Applications -> Accessories -> Terminal), and entered


sudo rm /usr/share/applications/avggui.desktop

AND IT GIVES AND ERROR MESSAGE:
rm: cannot remove `/usr/share/applications/avggui.desktop': No such file or director

tried second option

went to 
Click on "System-->Preferences-->Main Menu" To launch the menu editor. 
but cant find AVG anywhere there

come on guys i am new to this...

can any one guide me here... :(

---

### Post by paul.everett on 2009-11-11
Hi ,

I am trying out Ubuntu to see what all the buzz is about. I have used various flvours of Unix over the years but, not in the past 10 years or so and not on a PC. So I thought I'd give Ubuntu a try.

Overall I find i easy to use but, admit to getting lost when it comes to installing software. It just seems so difficult to do such a simple and frequent thing as add software to my PC!.

I have little problem if there is a package in a repository that Ubuntu knows about but, if it isn't there I seem to go round in circles working out how to install a .deb file that I have downloaded. I know I can install it by right-click and Open with GDEB etc but, is this best practice? Should I somehow add it to a repository first. I have noticed an option to add downloaded packages but, whenever I try to use it the option I want is greyed-out?

Anyway - I know a lot of Linux 'geeks'say that you don't NEED anti-virus - my response is Why does AV exist for Linux then ? I expect that as Linux gets more popular then Virus's WILL appear But, I digress. I decided for whatever reason to install AVG8.5. I downloaded the .deb file and installed it - so far so good - no errors. BUT, there is no entry in the menu's and no icon on the desktop - so how do I run it?

I did a search and found instructions on how to install AVG7.1 and some horrendous commands to type in Terminal JUST to get an Icon on the desktop. I mean that CAN'T be usual can  it ? I've worked in IT for years and am having trouble with it. Joe Average isn't going to move to Linux if it is this difficult to install a simple program !

Anyway anyone out there managed to get AVG 8.5 to run in a GUI? It must surely have GUI front end if AVG7.1 had one.

It doesn't matter that I'm trying to instal AntiVirus on Linux - this is relevent to any package that I might try to install. AVG only provide instructions on installing the package but, they give a dpkg command to type in Terminal. I tried that and got an message saying that it needed superuser privilege! I am the only user on the PC so surely I HAVE that privilege already ?

Any help greatly appreciated. I really WANT to like Linux but, this hassle is putting me off BIG time. As is the fact that there are SO many different Linux'x to choose from ! I thought Unix was Universal eXecutive - It's not very Universal with all these distros around !

---

### Post by Norwal on 2010-01-16
I tried AVG before and had this same problem.  I though I'd give it another try because I fix other people MS HHDs and find it handy to run AV on them from Ubuntu.  Again no luck. I had another AV running, BitDefender, and had no problems.  Check this threat out about the lack of GUI for 8.5
[http://ubuntuforums.org/showthread.php?t=1150039](http://ubuntuforums.org/showthread.php?t=1150039)

---

### Post by leorolla on 2010-01-16
If you open synaptics does it tell you the package is installed?

You can see the package properties and check which files are present, maybe there will be a binary that you can run, and maybe it also recommends/suggests other packages

---

### Post by jrusso2 on 2010-01-16
Its a command line application folks.

---

