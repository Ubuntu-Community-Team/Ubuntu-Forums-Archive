---
title: "failure on start up"
date: 2008-11-16
forum: Hardware
---

### Post by bleedpurple on 2008-11-16
I'm a pretty new user.  I have a gigabyte 7VT600 1394 motherboard with an AMD processor.  I got this computer from my son who also introduced me to Ubuntu.  I am completely sold.  Lately, however, the computer is failing to start.  When the start button is pressed the processor cooling fan starts and it appears to be starting, but then stops after about 2 seconds.  Nothing appears on the screen so I can't tell anything there.  I have to shut off power to the computer for a while before trying again.  This problem seems somewhat intermittent but is getting worse. I have already replaced the hard drive.

Does anyone have any ideas? Does this sound like a heat issue with the processor?  I know there is a thermal bonding agent between the processor and the heat sink. The AMD manual says this is important and needs to be replaced if the heat sink is removed. This has happened and I've not replaced it.  It doesn't seem logical to me that it could be overheating within 2 seconds and before it truly even starts. Is there a way to check if the issue is with the power supply?:confused:

---

### Post by 73ckn797 on 2008-11-16
> **bleedpurple said:**
> I'm a pretty new user.  I have a gigabyte 7VT600 1394 motherboard with an AMD processor.  I got this computer from my son who also introduced me to Ubuntu.  I am completely sold.  Lately, however, the computer is failing to start.  When the start button is pressed the processor cooling fan starts and it appears to be starting, but then stops after about 2 seconds.  Nothing appears on the screen so I can't tell anything there.  I have to shut off power to the computer for a while before trying again.  This problem seems somewhat intermittent but is getting worse. I have already replaced the hard drive.

Does anyone have any ideas? Does this sound like a heat issue with the processor?  I know there is a thermal bonding agent between the processor and the heat sink. The AMD manual says this is important and needs to be replaced if the heat sink is removed. This has happened and I've not replaced it.  It doesn't seem logical to me that it could be overheating within 2 seconds and before it truly even starts. Is there a way to check if the issue is with the power supply?:confused:

That would be the first place I would begin my diagnosis. If the heat sink is not fully making contact or not properly coated that would cause a problem.

---

### Post by finito on 2008-11-16
I agree with 73ckn797. can you tell me who fiddled with the heatsink, can you make sure that the cpu fan does start, from what you say it seems like you mean it sounds like it starts. If it was a power supply problem the computer wouldn't start.

when you say it starts for 2 seconds, and then you have to wait a while, this could also be due to a fried resistor although that is rare. 

If you can the best way to find out what is wrong is to completely strip the computer to the bare minimum, RAM, Motherboard, and Power. try to see if it works, then add the VGA (Video Graphics Adapter) if that is applicable as some motherboards come with VGA built in, see if everything is fine than add HDD then CD, and so forth.

If you encounter the problem with the bare minimum, than you will have to take it to a professional, or if you have spare parts lying around try interchanging them to try and make it work.

I know you said your a new user, but if your up to it try this. 

BTW if you take the motherboard completely out you can start the computer by running a metal object (i.e. screw driver) by the start jumper.

---

### Post by 73ckn797 on 2008-11-16
A faulty memory chip can cause strange behavior also. If you have several memory modules installed, do a process of elimination, remove all but one and restart. If the same problem occurs swap with another module ..... and so forth. But first address the heat sink issue.

If the motherboard has a LED that indicates power and if it stays illuminated then I would likely think the power is not the problem. Otherwise you could test the output following info that usually comes with the motherboard manual showing power pin-outs. Use a multimeter for this, checking the power supply harness plug going to the motherboard.

---

### Post by Olivier2371 on 2008-11-16
Hi there,

All the suggestion given above are correct but there is one missing. The power supply might be faulty. I had in the past the same problem, and I had to change the power supply.

Hope it is helpfull.

Good luck.

---

### Post by 73ckn797 on 2008-11-16
> **Olivier2371 said:**
> Hi there,

All the suggestion given above are correct but there is one missing. The power supply might be faulty. I had in the past the same problem, and I had to change the power supply.

Hope it is helpfull.

Good luck.


That was mentioned above.

---

### Post by Olivier2371 on 2008-11-16
> **73ckn797 said:**
> That was mentioned above.
Hi there, 

I apologies for my mistake. You are correct.

---

### Post by bleedpurple on 2008-11-16
> **finito said:**
> I agree with 73ckn797. can you tell me who fiddled with the heatsink, can you make sure that the cpu fan does start, from what you say it seems like you mean it sounds like it starts. If it was a power supply problem the computer wouldn't start.

when you say it starts for 2 seconds, and then you have to wait a while, this could also be due to a fried resistor although that is rare. 


The reason my son gave me the computer is he's a gamer and it wasn't good enough for him. He fooled with the CPU heatsink.  I took it to Geek Squad and they reapplied the thermal bonding agent. I reinstalled it.  I then pulled out all of the documentation for the gigabyte 7VT600 1394, his case, the AMD athlon processor and tried to go back to his original setup.  He had one of the temp sensors disconnected. It currently is running. I'm using it to type this email.  The led for the memory does light up if that means anything to you. I still suspect the power supply. It is 400w. I noticed in the power mgmt area of the bios that the 5v is running at about 4.9v.

---

### Post by bleedpurple on 2008-11-16
> **Olivier2371 said:**
> Hi there,

All the suggestion given above are correct but there is one missing. The power supply might be faulty. I had in the past the same problem, and I had to change the power supply.

Hope it is helpfull.

Good luck.

Olivier2371: When you say you had the same problem, did your system also start intermittently and sometimes for only a few seconds?

---

### Post by 73ckn797 on 2008-11-16
> **bleedpurple said:**
> The reason my son gave me the computer is he's a gamer and it wasn't good enough for him. He fooled with the CPU heatsink.  I took it to Geek Squad and they reapplied the thermal bonding agent. I reinstalled it.  I then pulled out all of the documentation for the gigabyte 7VT600 1394, his case, the AMD athlon processor and tried to go back to his original setup.  He had one of the temp sensors disconnected. It currently is running. I'm using it to type this email.  The led for the memory does light up if that means anything to you. I still suspect the power supply. It is 400w. I noticed in the power mgmt area of the bios that the 5v is running at about 4.9v.


I do not think that 0.1 volt will make a difference. There are parameters within which electrical systems are allowed to function.

If you are writing this from that computer, which seems to be my assumption:
> **bleedpurple said:**
> I'm using it to type this email. then maybe the problem is corrected. Or, is the computer not working? How are you sending this message?

---

### Post by 73ckn797 on 2008-11-16
> **Olivier2371 said:**
> Hi there, 

I apologies for my mistake. You are correct.

Not a problem at all, my friend.

---

### Post by Olivier2371 on 2008-11-17
> **bleedpurple said:**
> Olivier2371: When you say you had the same problem, did your system also start intermittently and sometimes for only a few seconds?
Yes bleedpurple. 

I had quite a lot of crashes a long time ago, when I was using my 286 copmuter.
Now I try to make sure that I have the right equipment.

---

### Post by bleedpurple on 2008-11-17
Perhaps the problem is corrected and it was due to a short or something.  There was a temperature sensor which was disconnected and the two leads could have shorted together if they were touching the case.   I think I will just keep an eye on it and if I have some more trouble I will replace the power supply.  I agree that the 0.1V makes no difference, I was wondering if that was a symptom of issues however.  All of the other voltages exceeded their targets 3.3/3.45, 12/12.2 etc.  I think the hard drive runs on the 3.3V rail doesn't it?

---

