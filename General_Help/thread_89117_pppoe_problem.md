---
title: "pppoe problem"
date: 2005-11-11
forum: General Help
---

### Post by cymoril on 2005-11-11
hi there,

i installed breezy today and i've experienced problems with pppoe.

i first enabled pppoe by doing "sudo pppoeconf"

all was fine and i chose to have pppd start at bootup.

it didn't start the next time i booted up.

when i did "ifconfig" i saw nothing.

i had to set it up again. and i have to keep doing this everytime i wish to use the internet.

the only thing i noticed when i shutdown the computer was " deconfiguring network - fail "

thanks for reading and thank you for your help.
cymoril

---

### Post by adwait on 2005-11-11
Once you have setup your connection, you can start it up with
```
sudo pon dsl-provider
```
and turn it off with
```
sudo poff
```

If the connection won't start on boot, just add the pon command to a text file. Make it executable using
```
chmod +x <filename>
```
Put it in the /etc/init.d/ directory. Then run
```
sudo rcconf
```
select the file you created and save changes. That file will now be run every time your computer boots.

---

### Post by cymoril on 2005-11-11
thanks, i'll try that.

i didn't have such trouble with hoary.
i can't remember if i set up pppoe with pppoeconf though.

is pppoeconf what everyone uses?

any idea why it didn't start up at boot when it clearly prompted me to select "yes" if i wanted that option?

thanks,
cym.

---

### Post by adwait on 2005-11-11
Yeah everyone uses pppoeconf (to the best of my knowledge.) About what it won't start......I dunno, sometimes it does that :p

---

### Post by trash on 2005-11-11
Have you upgraded since you installed? There is a for pppoeconf but i am not sure if it is on the install cd.

---

