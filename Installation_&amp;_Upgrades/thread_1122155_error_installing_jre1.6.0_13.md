---
title: "error installing jre1.6.0_13"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by marquis-de-carabas on 2009-04-10
Okay. First I downloaded the binary from the java website.  I put it into /opt/java/ on my desktop.  I changed the permissions on the file to a+rwx.  Then, I used cd to get to the /java and I executed the file with the command:
./jre-6u13-linux-i586.bin
I accepted the terms of aggreement and it installed, generating a folder called jre1.6.0_13 in /java
Now I am trying to set this runtime env as the default but i have hit a snag.  I did this:
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/jre1.6.0_13/bin/java" 1      /*all on one line*/
sudo update-alternatives --set java /opt/java/jre1.6.0_13/bin/java

the first command worked but the second spits out this message:
update-alternatives: Cannot find alternative `/opt/java/jre1.6.0_13/bin/java'.

Does anyone know why this may be?
I run Ubuntu Hardy using i believe 32 bit.
I am relatively new at this.

---

### Post by cariboo on 2009-04-10
I would suggest that you installed the ubuntu-restricted-extras meta package, this will install Flash, java, mscorefonts and most of the codecs needed to play most audio/video media. THe ubuntu-restricted-extras meta package is in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by marquis-de-carabas on 2009-04-10
I actually tried that before and after installing I used the tool on java's website that detects java on your computer and it said it couldn't find it.
Also, the new things weren't listed in firefox 3.0.8's add-ons menue located at Tools->Add-ons.  Do you have to do something to get the packages contents into firefox?

---

### Post by taurus on 2009-04-10
What's the output of this command from a terminal?

```
uname -m
```

---

### Post by marquis-de-carabas on 2009-04-10
i686
Do I need to uninstall other java's like icedtea before the new one will work?

---

### Post by taurus on 2009-04-10
Sometimes you need to reboot your machine.

---

### Post by marquis-de-carabas on 2009-04-10
okay I restarted it didn't work.

I looked at my installed programs list and I have the following:
Sun Java 6 Runtime
Sun Java 6.0 Plugin
OpenSDK Java Runtime
Icedtea Java Plugin
ubuntu restricted access thing you had me download.

Are any of these jse1.6.0_13 or would any of these prevent it from working.  Is there any other way to set jse1.6.0_13 to default?

---

