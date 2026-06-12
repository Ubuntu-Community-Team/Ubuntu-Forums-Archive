---
title: "Synaptic error HELP!"
date: 2008-07-14
forum: General Help
---

### Post by Bout to Snap on 2008-07-14
E: Type '--01:04:38--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I got this error after trying to install a deb package of wine, however I already had the package I suppose in the manager because this is what happened, I eventually did get wine installed and working fine,but i still get this error...how should i fix this? hope it's easy IMA NOOB.

---

### Post by Elfy on 2008-07-14
Run this in a terminal an dpaste the whole output please - and yes it shouldn't be too hard...

```
cat /etc/apt/sources.list.d/winehq.list
```

---

### Post by Bout to Snap on 2008-07-14
--01:04:38--  [http://wine.budgetdedicated.com/apt/sources.list.d/etch.list](http://wine.budgetdedicated.com/apt/sources.list.d/etch.list)
           => `etch.list'
Resolving wine.budgetdedicated.com... 81.171.111.184, 2001:4de0:aaac:0:2456::2
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 160 [text/plain]

    0K                                                       100%   24.35 MB/s

01:04:39 (24.35 MB/s) - `etch.list' saved [160/160]

Hope that helps.

---

### Post by jomiolto on 2008-07-14
> **Bout to Snap said:**
> E: Type '--01:04:38--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I got this error after trying to install a deb package of wine, however I already had the package I suppose in the manager because this is what happened, I eventually did get wine installed and working fine,but i still get this error...how should i fix this? hope it's easy IMA NOOB.

It seems that something inserted a time stamp or something like that in that above file (it should only contain a list of places where to look for packages). Can you post the contents of the /etc/apt/sources.list.d/winehq.list file?

Also, what steps did you go through while installing the Wine package? If it involved editing the above file, you should be able to fix it by changing the file to contain only the below line:

```
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
```

---

### Post by Elfy on 2008-07-14
Are you trying to add the debian etch repos - what are you using debian or ubuntu - or was it accidental as they are on the same page.

In the meantime delete the file with this command

```
sudo rm /etc/apt/sources.list.d/winehq.list
```

If you want to add the repo tell me and I'll help that after.

---

### Post by Bout to Snap on 2008-07-14
How do I view the contents? and also that second command was unrecognized. I'm completly stumped on what to do.

---

### Post by Bout to Snap on 2008-07-14
> **forestpixie said:**
> Are you trying to add the debian etch repos - what are you using debian or ubuntu - or was it accidental as they are on the same page.

In the meantime delete the file with this command

```
sudo rm /etc/apt/sources.list.d/winehq.list
```

If you want to add the repo tell me and I'll help that after.




2 words...( you pwn) thanks a bunch for the help! cant remember what exactly I was doing when i got this error so i cant provide much detail on it sorry.

---

### Post by Elfy on 2008-07-14
> 2 words...( you pwn) thanks a bunch for the help!just what does you pwn mean?

Need to know what version of ubuntu you are using or is it debian?

---

### Post by Bout to Snap on 2008-07-14
Using Ubuntu Feisty 7.04? Just installed like 2 days ago actually...had it installed b4 and then deleted it because of gaming issue's resently installed it using the duel boot methode and trying to get back in the hang of things unfortunatly most of the utilities that I download and try to install I come across dependancy's not meet and I think that's what i was doing when I caused that error. Is there any easier way to update libs? from what i can tell has to be done manually correct?

-oh and pwn means u totally kick the issue's ****.

---

### Post by jomiolto on 2008-07-14
Seems that I was too slow to post and forestpixie got first :p You can ignore my earlier message.

---

### Post by Elfy on 2008-07-14
Ok - don't run the commands then - you could get problems I'm not sure don't actually use wine.

As long as you have run the sudo rm /etc/apt/sources.list.d/winehq.list command you shouldn't get anymore problems. Run this to make sure

```
sudo apt-get update
```

If you get an error after that then post it here - all of the error.

Edit - you can get a version of wine for feisty here 

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

This is the most up to date version

[http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_1.0.0~winehq0~ubuntu~7.10-2_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_1.0.0~winehq0~ubuntu~7.10-2_i386.deb)

---

### Post by Elfy on 2008-07-14
Do you know that Fesity is unsupported after October.

---

### Post by Bout to Snap on 2008-07-14
> **forestpixie said:**
> Do you know that Fesity is unsupported after October.

Possible to upgrade with what i have now instead of a new complete download?

and thanks yeah my problems are solved.

---

### Post by Elfy on 2008-07-14
AFAIK you would have to upgrade twice - once to gutsy and then to hardy, which is supported for 3 years.

As well I think that you would likely end up downloading more than if you got the isos.

You might be better of doing a clean install rather than an upgrade especially if you've not done much to your install.

You could of course order a cd instead of downloading it.

---

### Post by Bout to Snap on 2008-07-14
> **forestpixie said:**
> AFAIK you would have to upgrade twice - once to gutsy and then to hardy, which is supported for 3 years.

As well I think that you would likely end up downloading more than if you got the isos.

You might be better of doing a clean install rather than an upgrade especially if you've not done much to your install.

You could of course order a cd instead of downloading it.

So basically I could just go straight to hardy? i wouldnt have to fool with gutsy at all correct? i dont mind downloading ISO's wouldnt take but about 20-25 mins at most, But I'll have to back up a few files first and then do a new clean install of hardy I suppose. Oh and do you have a link to hardy? or where can i find some info about what's new with it and stuff?

---

### Post by Elfy on 2008-07-14
Yes you can go straight to hardy with a clean install - here is download page.
[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

There is some info on what's new here [http://www.ubuntu.com/products/whatisubuntu/804features/](http://www.ubuntu.com/products/whatisubuntu/804features/)

If you have a seperate /home partition you could keep that and your data, if so it'd be worth sorting out the configs.


Could you mark thread solved as well please :)

---

