---
title: "[SOLVED] beep sound and blackout help needed .thanks"
date: 2008-11-26
forum: General Help
---

### Post by cmay on 2008-11-26
hi. i just finished in another tread a install of ubuntu 8.1.0 and happy as i was i marked the tread sovled while fetching the updates. it took just five minutes for the computer run ubuntu 8.1.0 and then give up and start to give a couple of beep sounds and then a black out . the screen is black now and it cant start. can anyone help me. its a 2 year old computer i have promised to fix that had a virus in a windows xp install. 
thanks very much

---

### Post by cariboo on 2008-11-26
You may have to try Ctrl-Alt-F1 to get to the console and then shutdown the computer, at the prompt type:

```
sudo shutdown -r now
```

This will reboot the computer. Restart in recovery mode and at the menu selec xfix, once it has run, select resume. This should get you up and running again. You will prpbably have to reinstall the restricted graphics drivers.

Jim

---

### Post by cmay on 2008-11-26
thanks.
it does not work however.  it just stands there now after a half hour and is blocked. nothing responds at all  .its just frozen on the start up screen. the first reboot i did worked for around five min then it started beeping and now its frozen and i cant get it to respond to hitting any keys at all.

---

### Post by cmay on 2008-11-26
OK. after much kicking and screaming i got it working by once again yank the battery out of the motherboard. i am not sure i can get this fixed even if i really have tried all that i can. its the computers blame and not mine or ubuntu thats all i am sure of right now.
anyway thanks for the time. i will post if i find some solution.

---

### Post by cmay on 2008-11-26
:confused:
i quit.
it will only do the same thing as it did when i got it out here. it will not start up and when the bios has been reset it works until shutdown. then it start up black screen and same thing as it did with windows in it. i am lost on this one and its over my bedtime so i simply think i will have to say i cant fix it. 
thanks for the help though.

---

### Post by cmay on 2008-11-27
this morning i found an solution. i simply disabled the bios password and let it have the default settings. then i let ubuntu stand loading moaning and groaning for an hour and suddenly it popped a message it had fixed some bad disk blocks on devise sdomething something i did not even have time to read and it works perfect as of now. 

thanks for the help everyone. also in the other tread. i am gratedul that i can save the enviroment for trashing a perfectly fine old compy.
i can honestly say this one was a battle but i won in the end. :)

---

