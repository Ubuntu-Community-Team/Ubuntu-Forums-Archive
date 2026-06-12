---
title: "toshiba a305d  heating problem in 9.04"
date: 2009-12-06
forum: Hardware
---

### Post by n2sins on 2009-12-06
has anyone found the problem to this . i have been going through ubuntu everyday and trying new things to try to isolate and remove this overheating problem.. i posted it to [B]HOWTO Fix A Buggy DSDT File 
[http://ubuntuforums.org/showthread.php?t=1036051&page=39](http://ubuntuforums.org/showthread.php?t=1036051&page=39)

so far nothing works.. anyone with an idea i will try.. thnx.
at first, i thought it was a buggy dsdt and it may still be.. but i am trying everything else too.. as my dsdt file had no errors or warnings. i also tried installing toshutils and the other one.. but not got the laptop to cool. i added acpi_osi="Linux" to the grub and that corrected several things it appears but the cooling isnt one of them.. i even done a dmesg on my dual boot vista with 9.04 and then a live cd of 8.10 and the thermal zones temps didnt match.. 9.04 reported 3 degrees higher then 8.10 not much by why is it diferent? anyone that can help i would much appreciate it.. im new to linux as an everyday user and eventhough i have used linux a while.. i am not a guru.. so please help.. thank you
[/B]

---

### Post by n2sins on 2009-12-10
i was wondering if anyone has noticed this.. i saved my dmesg file and was experimenting with things to help control the temperatures.. i found that each time i boot my thermal zone changed by as much as 20 some degrees.. at first my thermal zone always was 65c now it has been as low as 41c and its right now its 58c.. the only thing that changed was i re-booted pc.. when it rebooted it didnt recognize my gsm dongle for internet and reported all kinds of errors in dmesg.. i unplugged it and waited.. reinserted and finally after several tries my internet worked.. then i saw my thermal zone at 41c.. i rebooted and now its 58c.
has anyone noticed that..i thought it was weird to report differently on every boot.. is that normal
thanks..

---

### Post by n2sins on 2009-12-10
nevermind.. i thought that the thermal zone was a setting for cooling not a snapshot of the current status of the machine.. sorry for asking a dumb question but i didnt know the answer... now i do and feel like a real noob without a clue

---

### Post by n2sins on 2009-12-14
[SIZE=2][COLOR=Red]i love my ubuntu 9.04........[/COLOR][/SIZE][COLOR=Red]..[/COLOR][SIZE=2][COLOR=Red] and heres my last post/rant[/COLOR][/SIZE][COLOR=Red] [/COLOR][SIZE=2][COLOR=Red]to prove it[/COLOR][/SIZE]
i know im not the smartest person.. never claimed it... i never thought i could be the expert of linux.. never wanted it.. never saw so many people who are smart and are experts unable to even give a [COLOR=Red]suggestion[/COLOR].. so with that, i see no need to post here again.  it never gets a response.. no reason to try to fix this heating problem.. it is [COLOR=Red]unfixable[/COLOR].. and when this pc melts down.. i wont buy into microsoft or apple for my next pc.. i will follow the  open source philosophy of freedom.... i will make the choice to be [COLOR=Red]pc free[/COLOR].. no viruses no crashes and no multi-month/year repairs.. pcs will be where they belong at a job or at a store.......i know what your thinking.. another windows convert cant take the time and learn linux.. you would be wrong to think that..i have played on linux since mandrake in the late 90s. after all this time motherboard resources cant be utilized correctly.and cant be fixed. open gl cant be utilized on 1 year old laptop because its now legacy. how many people would buy a car if the manufacturer only makes parts for it for 1 yr???..  i know alot has to do with hardware manufacturers... but, linux was put on many cell phones and the x-box of all things.. but not a [COLOR=Red]1 yr old laptop.[/COLOR]. linux has come a long way. but, now what????.. what can we do when we cant keep the pc from overheating. i came from windows.. but as i have read.. i think everyone has come from windows.. im not here trying to whine about it.. or get unneeded attention.. im quite fine and happy.. just not happy about turning my laptop into a steaming paperweight.. i know im going to be crucified here.. so let the party start.. one last thing. i know linux is free. i know i cant expect everything . .im not mad.. not upset.. just disapointed.. most windows users are raving and ranting and cursing linux as they run for their beloved windows.. then whisper im sorry honey it was a mistake. it wont happen again.. that linux never meant nothing to me... will you forgive me.. and microsoft will say of course.. here buy our new op sys.. it will make you feel safe and secure.. [COLOR=Red]not me.. i will stay with my 9.04 until it melts.[/COLOR].. then i will be free... pc free.. is that the way linux on a desktop will end? will it be remembered for all the good things or just remembered as unable to even control a[COLOR=Blue] system fan.[/COLOR] i have attached a screenshot for reference

---

### Post by n2sins on 2009-12-18
good news to a degree.. i found a work around.. im hoping others will get some relief to the heat using this.. ok i have the ata1: softreset failed (device not ready) error and i still can boot.. i just get the ugly message.. but to the point.. try to hibernate. thats when the ugly message occurs . then after that. suspend.. after both check your temps and cpu usage.. my cpu dropped  on moonlander game from 99% to anywhere between 10 and 20%.. also temps dropped from 80C to just under 70C.
now i was curious.. so i looked under acpi and for the first time my fan was in the on state.. so maybe i have a work around.. someone else please try and confirm if this works for you.. by the way i do have custom dsdt.. but when recompiling it stated 0 errors 0 warnings and 15 optimizations.. and now no cpu throttling as a result of custom dsdt but now my laptop is cooler.. it doesnt have any trips points even now.. but its cooler..:guitar:

i hope others will get theirs cooler as a result.. this is the only thing i found to work.. its not as cool as i would like but it isnt giving me errors or getting to 80 and locking up and having to hard boot.. let me know if this help

---

### Post by n2sins on 2009-12-18
i wanted to add dmesg and maybe someone with tech knowledge can understand why the fan works and changes speed after suspend.. and i checked it several times and it does work.. the only thing that stinks is after suspend must get to 80c before fan actually turns on then it cools the pc down.. right now at 46c. playing a game at 2ghz performance only gets it back to 80c no higher.. and after the game is over returns down sub 50c.. oh the dmesg does not show the fan in on state but it is.. i did see acpi errors.. in dmesg.. as well a couple other known errors.. anyways i hope that someone can benefit from this.. im also putting my dmesg after custom dsdt maybe that can help

---

