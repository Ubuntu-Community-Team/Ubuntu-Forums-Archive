---
title: "printer not working on wifi"
date: 2017-06-02
forum: Hardware
---

### Post by plymouth532 on 2017-06-02
Good day,
I am still very new at this. I have a HP laptop running Ubuntu 17.04. I have a HP ENVY 5530 printer. Ther printer works with the cable buit does not work with the Wifi. I have reinstalled the printer multiple times with no luck. I ran  the HP trouble code in the terminal and received 15 erriors. I am sending the screen shot, hope this can be helpful so I can get my printer to work.

Thanks ed

---

### Post by gordintoronto on 2017-06-03
I would install Synaptic Package Manager, then use it to install the missing dependencies.

Is the printer talking to your router? Even if it's not doing anything, there should be packets passing back and forth, and the router should be able to display counts of the packets.

---

### Post by plymouth532 on 2017-06-04
> **gordintoronto said:**
> I would install Synaptic Package Manager, then use it to install the missing dependencies.

Is the printer talking to your router? Even if it's not doing anything, there should be packets passing back and forth, and the router should be able to display counts of the packets.

Thanks Gordintoronto for your help. I have installed Synaptic Package Manager but need help on how to install missing packets. I am a little leary of causing more problems than I have.

The router shows a connection to the printer.

Again thanks,
ED

---

### Post by gordintoronto on 2017-06-04
The image in your first post showed the names of missing packages, beginning with libcups2, I think. You should be able to "search" and then select each item, then "apply".

As an aside, libcups2 was already installed on my system. Which version of Linux did you install? (I'm running 64-bit Xubuntu 17.04 as my daily driver.)

---

