---
title: "Seperating Offline Install &amp; Online Download"
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by Aliby on 2005-12-21
I need too glean some experience from those who have been using linux for some time. I will endeavour to explain what I want to do (based on a pure debian method) and then perhaps you can suggest some (better) ways of accomplishing the same thing on Kubuntu.:KS 

[COLOR="Blue"]I have a PC running linux [COLOR="Red"]{L}[/COLOR] that doesn't have a dedicated access to the internet and one that is running Windows [COLOR="Red"]{W}[/COLOR] (and doesn't run linux) but has a permanent connection to the internet - Uh? Yes that one is at work 8-[ (Hence the time efficient automated process). 
The Debian procedure is a s followings: 
[LIST=1]
[*][COLOR="Red"]{W}[/COLOR]Download the Packages from the mirror site using wget
[INDENT][COLOR="DarkGreen"][SIZE="2"]wget -N -nd -c -O ftp.is.co.za_linux_distributions_ubuntu_archive_dists_dapper_main_binary-amd64_Packages.gz ftp://ftp.is.co.za/linux/distributions/ubuntu/archive/dists/dapper/main/binary-amd64/Packages.gz[/SIZE][/COLOR][/INDENT]
[*][COLOR="Red"]{L}[/COLOR]Add them to the apt folder in linux
[*][COLOR="Red"]{L}[/COLOR]Use synaptic to select packages I want to install so that it completes a full dependency list and tells me what package downloads are required.
[*][COLOR="Red"]{L}[/COLOR]Extract that list
[INDENT][COLOR="DarkGreen"][SIZE="2"]dpkg --get-selections > ~/home/Programs/packages.txt[/SIZE][/COLOR][/INDENT]
[*][COLOR="Red"]{L}[/COLOR]Create wget script file
[INDENT][COLOR="DarkGreen"][SIZE="2"]awk '{print "wget -N -nd " $2 " " $1}' < /home/Programs/packages.txt > /home/Programs/wget-script.bat
[/SIZE][/COLOR][/INDENT]
[*][COLOR="Red"]{W}[/COLOR]Use that script file on the winows box to download all the required packages
[INDENT][COLOR="DarkGreen"][SIZE="2"]wget-script.bat[/SIZE][/COLOR][/INDENT]
[*][COLOR="Red"]{L}[/COLOR]Copy the packages from a flash drive to the Linux box, to a folder
[INDENT][COLOR="DarkGreen"][SIZE="2"]/debs/binary/DebianInstall/binary/
[/SIZE][/COLOR][/INDENT]
[*][COLOR="Red"]{L}[/COLOR]Run dpkg scan to update the available packages
[INDENT][COLOR="DarkGreen"][SIZE="2"]cd /debs/binary/DebianInstall/binary/
dpkg-scanpackages unstable /dev/null | gzip > unstable/Packages.gz
[/SIZE][/COLOR][/INDENT]
[*][COLOR="Red"]{L}[/COLOR]Reload packages and use synaptic to install the packages
[INDENT][COLOR="DarkGreen"][SIZE="2"]dpkg --set-selections < ~/home/Programs/packages.txt[/SIZE][/COLOR][/INDENT]
[/LIST][/COLOR]

Part of my difficulties start when [SIZE="2"][COLOR="DarkGreen"]dpkg-scanpackages[/COLOR][/SIZE] gives me the error that bash doesn't have such a command?

Any comments will be appreciated :???:

---

### Post by towsonu2003 on 2005-12-22
///edit2/// offf - count me in as one of the users who wanna know the response to this. especially this part:
> dpkg-scanpackages gives me the error that bash doesn't have such a command
(replied but was not relevant to question)

would this help: ```
sudo apt-get install apt-show-versions
apt-show-versions > installed
``` ? ( from [http://ubuntuforums.org/showthread.php?t=80974&highlight=xubuntu+cd](http://ubuntuforums.org/showthread.php?t=80974&highlight=xubuntu+cd) )

Note: We really need a wiki for this which should have much more options than [https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto) has (such as 
1. for those who have net connection only on another debian / ubuntu box
2. for those who have net connection only on a win compuer
3. for those who have dial up on target ubuntu box and fast connection on win computer
4. etc...

---

### Post by az on 2005-12-22
[QUOTE=Aliby]
Part of my difficulties start when [SIZE="2"][COLOR="DarkGreen"]dpkg-scanpackages[/COLOR][/SIZE] gives me the error that bash doesn't have such a command?

Any comments will be appreciated :???:[/QUOTE]

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=dpkg-scanpackages&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=dpkg-scanpackages&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)

dpkg-scanpackages is in the dpkg-dev package

apt-show-versions is for a mixed-released installation (like breezy and Dapper) which may not be relevant here.

Some people want to improve the  packages.ubuntu.com website to add this sort of functionality to it.  Like a "download all dependancies" button.  Some have also discussed writing a windows script to resolve dependancies on a different platform so that you can do this.

---

### Post by Aliby on 2005-12-22
*[COLOR="Orange"]Just to note that i have done alot of reading and taking notes - rather theoretical at this stage and only now am I starting to get my keys dirty ... i.e. I am not very experienced with Linux, just have learnt some of the concepts and of course some of the buzz words[/COLOR]* :p 

Sorry, I never did sufficient homework ... regarding the bash "error" saying it doesn't know how to respond to the "dpkg-scanpackages" command. It was simply because I never had it installed! I found out eventually that it is part of the dpkg-dev package using "Search the contents of packages" on the Packages website ([http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=dpkg-scanpackages&searchmode=searchfiles&case=insensitive&version=breezy&arch=amd64](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=dpkg-scanpackages&searchmode=searchfiles&case=insensitive&version=breezy&arch=amd64))

THanks **azz** ... at least I am learning how to find where what belongs. I am making some progress!:KS

---

### Post by Aliby on 2006-01-16
NOte that synaptic have added a new menu command under "File" that creates a download script: "Create Download Script".

This is basically a wget script that you can use on "any" system as there are wget binaries available. A great add from the Synaptic team - you rule :KS . 

*I just would like the option to append options to the wget file OR if the "-c" option (which enables continuing an incomplete download) is added by default*

So you just need to "dpkg-scanpackages" to update your own repository "Packages.gz" file so that synaptic sees the newly added files - things are really getting simplier! :razz:

---

### Post by ingo on 2006-12-13
ok, better late than never... here is the REALLY SIMPLE solution

[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)

---

