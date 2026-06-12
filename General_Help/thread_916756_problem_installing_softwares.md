---
title: "problem installing softwares"
date: 2008-09-11
forum: General Help
---

### Post by zohaib on 2008-09-11
****whenever i try to install any software i get an error massage it says "Only one software management tool is allowed to run at the same time"  but no other application is runing an the same time so why im getting the same massage??., 
I've tried it so many times., it gives me the same massage again and again.,
i also restarted my computer many times but i get the same massage.

can any1 tell whats the problem.

i'm new to ubuntu so i dont know much about it, any type of help will be appreciated thanks.

---

### Post by hwttdz on 2008-09-11
Open a terminal and try running "top -b -n 1" and post the results here.  This command tells you what programs are running, I would be looking for something like apt-get, synaptic or one of the other programs that can get a lock.

---

### Post by zohaib on 2008-09-11
> **hwttdz said:**
> Open a terminal and try running "top -b -n 1" and post the results here.  This command tells you what programs are running, I would be looking for something like apt-get, synaptic or one of the other programs that can get a lock.

thanks for the response friend, but there were so many programs runing in the terminal, how can i know that which application is stoping me to install softwares??

any hint?

thanks.

---

### Post by hwttdz on 2008-09-11
That's part of the reason why I asked you to post it here.  Although I told you what I would be looking for so that you could try on your own as well.  I recommend posting the whole thing, because even if I can't identify the problem someone else may find that information useful.  

If you want to try yourself in addition you can try that command and piping the output to grep for synaptic, or apt.  Such as
top -b -n 1|grep -E "synaptic|apt".

---

### Post by zohaib on 2008-09-11
let me explain some more.

yesterday i was installing lime wire pro so it asked me to download Java, the installer downloaded Java by itself, the Java installation was taking so much time more than an hour,[that's also a problem which im facing] then after a while electricity went and then when electricity came i turned on my pc and tried to install Lime wire pro again this time it showed me that massage which I've discussed in my first post. which is "Only one software management tool is allowed to run at the same time"


I think I Should re-install my ubuntu.

---

### Post by kokkus on 2008-09-11
Ahh the limewire bug is classic.
OK open add/remove programs, add a program to install and then you get an error with a terminal code.
Type this code in the terminal.
Then type this line in terminal: sudo apt-get install ubuntu-restricted-extras
This will reinstall java and now the problem is out.

Now, here's the limewire installation file that works:
[http://scumbox.com/ubuntu/LimeWireLinux.tar.gz](http://scumbox.com/ubuntu/LimeWireLinux.tar.gz)

---

### Post by hwttdz on 2008-09-11
Try "sudo synaptic" at the command line and see if it gives any output.  What I'm hoping for is an informative error. 

I know that mozilla creates a profile lock, which when things crash can (or at least could in the past) prevent one from opening new mozilla.  

If you just installed reinstalling sounds not a bad plan.  But it would be nice to figure out in case someone who has years of data has the same problem.

A few more things to try:
apt-get clean (I don't think this will help, but I think it would remove the partial java download)
apt-get install -f
dpkg --configure -a

---

### Post by zohaib on 2008-09-11
I can't see any add button in the add/remove program

hey thanks for your help I really appreciate that buddy.

---

### Post by hwttdz on 2008-09-11
Checked boxes are installed, unchecked are not.  To install a new program find an empty box and then mark it and hit apply changes.

---

### Post by zohaib on 2008-09-11
when i add a program i get this error massage "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

i when i paste it in terminal it says "bash: syntax error near unexpected token `('"

still dont know wat the exact problem is

hey can you come on yahoo here is my yahoo id "fearfulll@yahoo.com"

---

### Post by kokkus on 2008-09-11
And that's what u do. run this in your terminal:
dpkg --configure -a

---

### Post by zohaib on 2008-09-11
> **kokkus said:**
> And that's what u do. run this in your terminal:
'dpkg --configure -a

i type that in terminal it says "dpkg: requested operation requires superuser privilege".
nothing else happens.

---

### Post by kokkus on 2008-09-11
are u in root terminal now?

Sorry, type it in root terminal

---

### Post by zohaib on 2008-09-11
> **kokkus said:**
> are u in root terminal now?

Sorry, type it in root terminal

where root terminal is located?

sorry for asking everything, im new to ubuntu so i dont know anything about it thats why im asking everything. dont mind.

---

### Post by kokkus on 2008-09-11
It's ok. I remember when I was a newbe in linux.
OK, right click on the application menu, click on edit menus.
Now under the category System Tools, mark root terminal. 
It's unmarked as default.

---

### Post by zohaib on 2008-09-11
yea i got root terminal thanks
 hey i type it in root terminal it says"Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ..."

wats does that mean?

---

### Post by hwttdz on 2008-09-11
It means you win.  Try using synaptic or add remove again, it should work.

Additionally if you want to run a command as root, but don't want to use a root terminal, just add sudo in front of the command.  I.e. to say hi, instead of "echo hi" you say "sudo echo hi".  See 
[http://xkcd.com/149/](http://xkcd.com/149/).

---

### Post by kokkus on 2008-09-11
WHen u installed limewire, the java runtime crashed because of a crossinstallation of a package u already had, because the java package in limewire.deb was currupt. 
So to be short, the problem should be solvd now.
SO now do as I suggested to to on the first page.
Install the ubuntu extras thing in normal terminal. and then use the package link I gave u to install limewire.

---

### Post by zohaib on 2008-09-11
i think java is being installed

after i type this it shows some dones in the terminal n then it shows this on a blue screen "                                                                           &#9474;  
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;  
 &#9474;     form, any other machine readable materials including, but not         &#9618;  
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>

---

### Post by kokkus on 2008-09-11
TO ender ok on the license, use the TAB key till u see the ok button is marked red.
Then click the return button to enter the license.

---

### Post by zohaib on 2008-09-11
oh yea its working its installing java

i've entered ok after highliting ok by pressing the tab button ., 

thank you so much

---

### Post by kokkus on 2008-09-11
No problem. Ok, now DO NOT use the limewire installation file from thair homepage. Use the link i gave u, unpack it, go to your normal terminal.
Type gksudo nautilus, then u get a filebrowser up, use it to manage the unpacked limewire folder. With nautilus, go to the location where u unpacked the limewire file, in the direcotry copy usr, go to filesystem and pasted it there and say yes to move the files there.

---

### Post by zohaib on 2008-09-11
ok kool., java installation is still runing i think i should install limewire after the java installation.,

---

### Post by zohaib on 2008-09-11
i think java intallation is completed

it says "All done, no errors.
All fonts downloaded and installed.

Setting up sun-java6-jre (6-00-2ubuntu2) ...

Setting up sun-java6-bin (6-00-2ubuntu2) ...

Setting up sun-java6-plugin (6-00-2ubuntu2) ...

Setting up ubuntu-restricted-extras (2.2) ..."

---

### Post by zohaib on 2008-09-11
limewire n java installation has completed now i im using limewire.

thanks u so much for your help.,

---

### Post by kokkus on 2008-09-11
Yup. sounds fantastic. Everything seems to work fine for u now.
If the manually installation method for limewire is hard for u to understand, go to [www.getdeb.net](www.getdeb.net) and download / install frostwire which is exactly the same with design and everthing but with less spam links when u search, coz it is the pro version of limewire.
Getdeb.net is a great website with easy installation packages. 
.deb is not an archive as .gz. deb is an installation package format for linux.

EDIT: My message came too soon I suppose hehe.
But glad I could help you :)

---

### Post by zohaib on 2008-09-11
yea i've used frostwire its pretty kool, but im in love with limewire:)hehe.

one more question can i install bittorrent from the file browser just like i've installed limewire?

---

### Post by kokkus on 2008-09-11
U mean install it manually? why would u do that when u can install it automaticly by using add/remove programs.
BUt if u want u can do it by just download the package and not install it, extract the .deb file and move the folders.

Ps. I too love limewire :)

---

### Post by zohaib on 2008-09-11
yea bittorrent client is already installed in ubuntu but its not wat i want.,i want original bit torrent client.
i cant remove default bitterent from add/remove.

when i uncheck it , it says "Cannot remove 'gnome-btdownload'
One or more applications depend on gnome-btdownload. To remove gnome-btdownload and the dependent applications, use the Synaptic package manager."

---

### Post by zohaib on 2008-09-11
problem solved., i've installed ktorrent n this is wat i wanted,:):):)

---

### Post by kokkus on 2008-09-11
Use synatic package manager. Search for bittorrent and unmark it there.
Since you are removing a program thats already inuse, I suggest u to reboot the pc so all settings to the program will be cleaned up. Now you can install another bittorrent. Personily I use ktorrent.

EDIT: I'm allways too soon hehe:)

---

### Post by zohaib on 2008-09-11
ok im going to reboot my PC

---

