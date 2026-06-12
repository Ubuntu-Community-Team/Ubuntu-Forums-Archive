---
title: "Acer Aspire 5315 overheat"
date: 2011-07-19
forum: Hardware
---

### Post by sm1thson on 2011-07-19
**Edit: skip to post 4, reading the first post may be a waste of time Id rather you skip to post 4 and help me :)**

I attempted to put my neigbours Acer Aspire 5315 onto ubuntu 11.4] but it cut off during installation, I realised it was overheating (googled and it is a common problem on anything other than its original windows vista (*,) ).

One way round this is to update the bias, but a lot of people have bricked their machines doing this and I dont want to brick my neighbours laptop. so right now it is sat on icepacks.

there is an old thread (archived) with the most useful post being here: [http://ubuntuforums.org/showpost.php?p=4925392&postcount=117]("http://ubuntuforums.org/showpost.php?p=4925392&postcount=117") I have followed this step by step (i think). 

My first problem is it gave errors that it wasnt finding the mempat file so I moved both the script and mempat to the /usr/bin as thats where they need to be when ran automatically, but I havent added the script to the rc.local yet as it doesnt work when i run it manually. Putting the files in /usr/bin cleared some errors but still when I run the script: 

sudo ./acer_fancontrol

the script runs but the fan doesnt spin and I get the error:

./acerfancontrol: 149: cannot create /proc/acpi/thermal_zone/TZ01/polling_frequency: Directory nonexistent 

followed by other errors:
/proc/acpi/Temperature: no such file or directory 


browsing the folders on the computer under /proc/acpi/ there is no thermal_zone folder :(

I tried to make one by navigating there in terminal and typing 

sudo mkdir thermal_zone 

but I get the error of 

cannot create directory 'thermal_zone': No such file or directory.

so no I am stuck. after spending all night on next doors machine, which is depressing as the actual ubuntu install took less than 15 mins off the USB drive (which I was quite impressed with).

---

### Post by sm1thson on 2011-07-20
I think I will have to add the sensors package first, I'll try that tonight (if i get time)

sudo apt-get install lm-sensors
sudo sensors-detect

---

### Post by sm1thson on 2011-07-21
Ive added the sensors package as per the second post above, the fan is now spinning is it likely that I wont need to do all the stuff in the first post, ie have ubutu now added something to control the temp once the sensors are installed? 

I have taken it off the ice to test, but it would be ice to know before handing the laptop back, as I dont want it to be a case of it working fine for me tonight then dying on the neighbour when they do something processor intensive.

I might go look for some monitoring software at least then I can see whats going on.

---

### Post by sm1thson on 2011-07-21
ok with sensors installed I can check the temp by typing

sensors

i terminal, it seems to run at 65-70c which seems high and the fan doesnt change speed, so it looks like i can monitor the fan, it is now on, but isnt controlled. 

The methods I have found all seem quite dated, yet the problem of people having heat issues on laptops is still common, but I havent yet found an uptodate answer on solving this (I have retried the stuff in the first post now sensors is installed, but no joy, same output as there is still no  thermal_zone folder in /proc/acpi/)

---

### Post by sm1thson on 2011-07-21
ok to recap lmsensors is installed.
I have run sudo sensors-detect and answered yes to everything then rebooted.

I have now installed fancontrol

but typing 

pwmconfig 

gives "there are no pwm-capable sensor modules installed"

Time for bed if anyone can help it would be much appreciated.

---

### Post by mörgæs on 2012-07-30
In case someone googles the thread: Ubuntu 12.04 runs well without overheating.

Hereby closing.

---

