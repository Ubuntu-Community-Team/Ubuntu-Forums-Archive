---
title: "Dell Laptop Cooling i8kfangui"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by Mr_bleu on 2007-06-03
Download dellfand:   [http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)
Save to Desktop.
Go to:   system>administration>synaptic manager
Install g++ (I clicked the Search button and typed it in)
Untar the file (I'm a former windows user so I double click, then extract)
Open a terminal:
$cd ~/Desktop/dellfand-0.7
$chmod a+x dellfand
$sudo cp dellfand /usr/bin
$sudo cp etc.default.dellfand /usr/bin
$sudo cp etc.init.d.dellfand
$sudo dellfand (This will display current fan status output and temp)
$sudo dellfand 1 10 25 35 43 (My personal settings for dellfan)
OR
$sudo dellfand 0 10 25 35 43 (This will output the status until the terminal is closed)
output from the above command:
Fan 0 Status 2->1 Speed 123960 CPU Temp 37C

Still haven't figured out how to get it to run upon boot.
Good luck everyone!!:popcorn::popcorn::KS:KS:KS

---

### Post by adampyre on 2007-06-05
Hello,

I placed "sudo dellfand" as a command in sessions and it loads it at bot up for me. Didn't prompt for a password though...strange....unless this is somehow managed through the keyring, which pops up for my wireless..... i don't know.

---

### Post by Mr_bleu on 2007-06-05
Thanks, I'm going to try that now. Will let you know how it turns out.

---

### Post by Mr_bleu on 2007-06-05
I believe it's working fine. Thanks for that tip.  I'm still learning linux.  I don't think I'll ever go back to windows except to repair  a computer or 2.

---

### Post by Mr_bleu on 2007-06-05
Download dellfand: [http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)
Save to Desktop.
Go to: system>administration>synaptic manager
Install g++ (I clicked the Search button and typed it in)
Untar the file (I'm a former windows user so I double click, then extract)
Open a terminal:
$cd ~/Desktop/dellfand-0.7
$chmod a+x dellfand
$sudo cp dellfand /usr/bin
$sudo cp etc.default.dellfand /usr/bin
$sudo cp etc.init.d.dellfand
System>preferences>Sessions
Click New
select a name (I used dellfand)
In the command box: sudo dellfand
click okay.  You can change the above settings, these are the ones I prefer.
This will bet it to run at boot time.
$sudo dellfand (This will display current fan status output and temp)
$sudo dellfand 1 10 25 35 43 (My personal settings for dellfan)
OR
$sudo dellfand 0 10 25 35 43 (This will output the status until the terminal is closed)
output from the above command:
Fan 0 Status 2->1 Speed 123960 CPU Temp 37C

Kudos to adampyre for the sessions startup tip.:popcorn::popcorn::popcorn::KS:KS

---

### Post by dyssident on 2008-01-04
Nice. You may very well have saved my new Vostro 1500 (although temp never got over 50 degrees).

Did the following commands to get v0.9 working as a first-class daemon, thus eliminating session setup.

First, download the latest archive from [http://dellfand.dinglisch.net/#download](http://dellfand.dinglisch.net/#download) to your home directory. Open a terminal and run:
```

tar xvf dellfand-*.tar.bz2
cd dellfand*
# Compile
make
# Install some files
sudo cp dellfand /usr/sbin
sudo cp etc.init.d.dellfand /etc/init.d/dellfand
sudo cp etc.default.dellfand /etc/default/dellfand
# Start the daemon
sudo /etc/init.d/dellfand start
# Make it start automatically
sudo update-rc.d dellfand multiuser

```

---

### Post by trondhuso on 2008-02-24
Someone should make this a package or get it into the repository. 

-trond-

---

### Post by himynameiskevin on 2008-02-28
i still haven't been able to get fan control working on my dell vostro 1000. i've tried i8k on windows as well, and it went nowhere. if anyone has any answers it would be much appreciated..

---

### Post by King_Louie on 2008-03-02
I just followed dyssident's install method for v0.9 on my Vostro 1400 running Hardy Alpha 5. 
"sudo dellfand" reports: v0.9: Fan 0 Status 1 Speed 78450 CPU Temp 33C. 
Looks like everything is working! Thanks to all.

---

### Post by Chimera76 on 2008-06-24
> **dyssident said:**
> Nice. You may very well have saved my new Vostro 1500 (although temp never got over 50 degrees).

Did the following commands to get v0.9 working as a first-class daemon, thus eliminating session setup.

First, download the latest archive from [http://dellfand.dinglisch.net/#download](http://dellfand.dinglisch.net/#download) to your home directory. Open a terminal and run:
```

tar xvf dellfand-*.tar.bz2
cd dellfand*
# Compile
make
# Install some files
sudo cp dellfand /usr/sbin
sudo cp etc.init.d.dellfand /etc/init.d/dellfand
sudo cp etc.default.dellfand /etc/default/dellfand
# Start the daemon
sudo /etc/init.d/dellfand start
# Make it start automatically
sudo update-rc.d dellfand multiuser

```

I can't TELL you how happy I am that this worked, thank you!

---

