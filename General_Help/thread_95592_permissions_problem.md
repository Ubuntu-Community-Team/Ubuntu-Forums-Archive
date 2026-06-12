---
title: "permissions problem"
date: 2005-11-26
forum: General Help
---

### Post by Fittersman on 2005-11-26
Whenever i try and edit some file or something it tells me permission denied but it prompts me for a password before that and i put it in then try to edit the file and it tells me permission denied.

example situations are i tried to gunzip scanModem and others that i cant remember

---

### Post by teaker1s on 2005-11-26
if it's a file other than one in your home directory you need to run
'gksudo nautilus' which gives root access to alter them.
generally 'gksudo' for any gui /'sudo' for console(allows you to act as root)

secondly if it's more widespread look here for help

[https://launchpad.net/distros/ubuntu/+bug/4738]("https://launchpad.net/distros/ubuntu/+bug/4738")

---

### Post by Fittersman on 2005-11-27
it tells me im not authourized to "startx" 

i tried your method and it gives me errors and stuff

when i first installed ubuntu i was able to use the command "startx" though i have previously edited the hosts file somewhere adn the xorg.conf file so if editing those is a problem please tell me

---

