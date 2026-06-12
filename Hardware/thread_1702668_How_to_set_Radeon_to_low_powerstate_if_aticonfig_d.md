---
title: "How to set Radeon to low powerstate if aticonfig doesn't recognize --set-powerstate ?"
date: 2011-03-08
forum: Hardware
---

### Post by MrPok on 2011-03-08
Hello Forum,

[INDENT]Short description:
**I am unable to set my ATI Radeon HD 4870 X2 in a lower voltage mode.** (fglrx & aticonfig) 
Default clockspeeds are way too high --> card gets hot --> gpu fanspeed too high --> unnecessary/annoying noise ! :shock:[/INDENT]

More specifically, I would like to lower both the GPU clockspeed (to the min. 507Mhz) and the Memory clockspeed (to the min. 500Mhz) to reduce the unnecessary heat the videocard produces, so the GPU fan can be switched off -- my ubuntu boot will be *as quiet as in Windows*. 

Per default, my videocard seems to run with high clockspeeds, the so-called "3D mode": the GPU at 750Mhz, Mem at 900 Mhz. 
(I read somewhere this might have to do with Compiz and/or X telling the driver to do so, but I don't believe a few destop effects require these heavy settings, so perhaps someone knows if I can add an exception somewhere?)

I am using the ATI/AMD propietary FGLRX graphics driver (version 2:8.780-0ubuntu2 according to synaptic)
Installed using "Additional Drivers" under System>Adminstration in Ubuntu 10.10 Maverick Meerkat 64-bit.

When I follow the instruction posted over the past years (and stated on [http://wiki.cchtml.com/index.php/Configuring#Changes_taking_effect_immediately](http://wiki.cchtml.com/index.php/Configuring#Changes_taking_effect_immediately)) I get errors:
```
$ sudo **aticonfig --list-powerstates** 
aticonfig: unrecognized option '--list-powerstates' 
aticonfig: parsing the command-line failed. 

$ sudo **aticonfig --set-powerstate=1** 
aticonfig: unrecognized option '--set-powerstate=1' 
aticonfig: parsing the command-line failed.
```
I noticed that *aticonfig --help* has some reference to *--set-powerstate*, but it almost seems like a "leftover" from a previous version of the help. (also mentioned in >[post]("http://ubuntuforums.org/showpost.php?p=9383681&postcount=31")<)

It almost seems like somewhere in 2010 aticonfig was downgraded... :confused:

--

Does anyone know how to throttle down my radeon, or have a reference to instructions?
If you require more system info to help me fix this, pls let me know! ;) (any feedback on how to improve my posts is also welcome)

Kind regards,
Paul

---

### Post by Yellow Pasque on 2011-03-08
Copy and paste commands to avoid syntax errors. The argument is:
```
--list-powerstate**s** ( or --lsp ) 
```

---

### Post by MrPok on 2011-03-14
> **Temüjin said:**
> Copy and paste commands to avoid syntax errors. The argument is:
```
--list-powerstate**s** ( or --lsp ) 
```
Unfortunately, this was just a typo in my post. I ran the command again and I still got the "unrecognized option", also with '--lsp'

Any ideas, anybody?

---

### Post by anantshri on 2011-04-09
I am also stuck with same please can anyone help.

commands are not working....

and Laptop is getting overheated.

---

### Post by mnrl on 2013-03-26
I have the same problem and i can't find a solution :(
in amdcccle PowerPLAY option works but  ```
[COLOR=#000000][FONT=courier new]mnrl@mnrl-K54HR:~$ aticonfig --list-powerstates [/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]aticonfig: unrecognized option '--list-powerstates'[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]aticonfig: parsing the command-line failed.[/FONT][/COLOR]
``` ](*,)

---

### Post by Yellow Pasque on 2013-03-26
mnrl: this thread is old and ati/amdconfig options/syntax may have changed in the past couple years. Try looking at the help for amdconfig:
```
amdconfig --help
man amdconfig
```

If you still can't figure it out, please make a new thread. I'm requesting this one to be closed.

---

### Post by wildmanne39 on 2013-03-26
Thread closed. Please do not post in old threads.

---

