---
title: "Freeze after kernel update"
date: 2005-11-23
forum: General Help
---

### Post by ikd69 on 2005-11-23
Friends,

after updating to 2.6.12-10, the system recommended rebooting and following that, it gets stuck.  Plenty of error messages to the effect that it can't find the hd(0,0) and then that I need to add a root option in the boot command.

I tried entering via the recovery mode from grub but ... zippo

1)I am now working with 2.6.12-9.  Is there a way to de-install the packages that the system recommended installing? and what are these packages?
2) How about fixing this kluge?

Thanks,

IKD

---

### Post by Pablo_Escobar on 2005-11-23
Mine k7 update went great, and I'm using the 2.6.10 kernel with modules without any fuss :)
What is Your kernel type that causeed these problems ??

---

### Post by ikd69 on 2005-11-23
[QUOTE=Pablo_Escobar]Mine k7 update went great, and I'm using the 2.6.10 kernel with modules without any fuss :)
What is Your kernel type that causeed these problems ??[/QUOTE]

Sorry, I should have been more detailed.

It is 2.6.12-10-386.  This is an old PIII@800MHz.  Nice little box, working fine so far :)

---

### Post by ceejay13 on 2005-11-23
Didn't want my first post to be like this :(  but feel this might add to the debate.

I have an Epia MS 1000E and the system is running, but it stalls (not hanging - graphics inteface runs but slowly) when it is doing the update.  I shut the system down, restarted and Synaptic won't run as dpkg 'has control'.  Running 'dpkg -a configure' as Synaptic suggested - it stalled again.  Pressing CTRL-C brought the thing through to the end and cleared the way for Synaptic to run again.

Attached is an image of my terminal screen with the messages from the 'ordeal'.  (Being a newb and just having spent a week getting a mail server running :lol: )

[ATTACH]3819[/ATTACH]

---

