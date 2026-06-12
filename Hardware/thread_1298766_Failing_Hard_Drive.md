---
title: "Failing Hard Drive"
date: 2009-10-23
forum: Hardware
---

### Post by patrickaupperle on 2009-10-23
Gnome just recently started giving me a warning about my failing hard drive. It says: ```
[COLOR="Red"]DISK HAS MANY BAD SECTORS[/COLOR]
```
I just want to make sure that there is no other option other than replacing the disk. I really do not want to buy another drive for my laptop. Should I replace, or is there another option?

PS. I use Arch Linux. I do not think it is an OS specific issue, and I like these forums better. That is why I posted here. If it does make a difference, it would be great if you could try to help anyway.

---

### Post by WolfRage on 2009-10-23
Some things I found.
[http://ubuntuforums.org/showthread.php?t=81565](http://ubuntuforums.org/showthread.php?t=81565)
[http://ubuntuforums.org/showthread.php?t=1261283](http://ubuntuforums.org/showthread.php?t=1261283)
[http://ubuntuforums.org/showthread.php?t=1004674](http://ubuntuforums.org/showthread.php?t=1004674)
 
It seems fsck is a minor fix... but the best fix is to get the hard drive vendors drive remapper... but the issue will not be fixed just delayed.

---

### Post by patrickaupperle on 2009-10-23
I think my drive is a Hitachi. Is there a remapper that does not delete all data? Having to start with no data is one of the biggest reasons (aside from cost) I do not want to buy a new disk. I really do not have a good back up system. It is good enough in case of emergency, but really not convienent.

---

### Post by WolfRage on 2009-10-23
Unfortunately the answer is no, in order to remap as the bad sectors are found the application must also reformat the drive. Best bet is to back up your home folder to include all of the hidden folders. Then write down all of your settings and applications. Remap and reinstall. Sorry.

---

### Post by quimkaos on 2009-10-23
well since it's OS independent maybe it's better (and since seams no one is able to call for an linux application that will fix your drive bad sectors) for you to download hiren's boot cd and use 1 of the many tools the cd has, just be carefull because some tools can kill you HD for good (if it's not already in the verge of death)... HDs are the worst part of any computer...

---

### Post by patrickaupperle on 2009-10-23
If I do reformat my HD, I will probably use Hitachi's tool for the job. Maybe, I will just use it till the sectors cause a severe problem. Keep good back ups. Then eventually just replace the HD. What issues could doing it this way cause?

---

### Post by quimkaos on 2009-10-24
basically a simple format wont solve you any problems with bad sectors, and they will be back. like fdsk in win/dos fsck will only instruct the HD to always jump over the affected sectors, ignoring them but not solving them. what i think wolf was trying to tell is to use tools from the manufacturer (Hitachi? try checking on you bios or in any lin tool - again with hirens you have lots of tools were you can get this info back),because usually manufacturer tools can fix problems that other software can't, and bring the drive "almost" to factory defaults. Back up your data, scan the drive off any operation system (mounted drives can't be fixed in some cases), then do a low level format. Reinstall everything.

BUT before anything of this think:
- is your laptop still under guarantee (in Europe it's 2 years minimum)?
- Are you dual-booting?
[INDENT]- did your laptop came with windows? with a cd or in an hiden patition were windows setup, drivers, and in some cases, system restore? if you do a full format all this will go away!
[/INDENT][probably to be continued] :biggrin:

---

### Post by patrickaupperle on 2009-10-24
> **quimkaos said:**
> basically a simple format wont solve you any problems with bad sectors, and they will be back. like fdsk in win/dos fsck will only instruct the HD to always jump over the affected sectors, ignoring them but not solving them. what i think wolf was trying to tell is to use tools from the manufacturer (Hitachi? try checking on you bios or in any lin tool - again with hirens you have lots of tools were you can get this info back),because usually manufacturer tools can fix problems that other software can't, and bring the drive "almost" to factory defaults. Back up your data, scan the drive off any operation system (mounted drives can't be fixed in some cases), then do a low level format. Reinstall everything.

BUT before anything of this think:
- is your laptop still under guarantee (in Europe it's 2 years minimum)?
- Are you dual-booting?
[INDENT]- did your laptop came with windows? with a cd or in an hiden patition were windows setup, drivers, and in some cases, system restore? if you do a full format all this will go away!
[/INDENT][probably to be continued] :biggrin:

Well, when I said format, I meant low level format with Hitachi's tools. My hard drive is behaving really wierd right now, would that low level bad sector skipping process make it act normal? Occasionally, The whole system will just freeze up with the hard drive light glowing solidy for about 45-90 seconds. Would skipping bad sectors stop this from happening? After that zeroing out (that I have referred to as a low level format), how long untill I would probably have to replace the drive anyway?

Edit: I think those questions were just for me to answer for myself, but I will post the answers up here just in case. This hard drive is a second hard drive I bought just for putting linux on. My Windows hard drive is small, and it was full at the time. So, this one came completely blank. I do not have to worry about the dual booting/Windows issues. Also, the laptop is still under it's warranty period, but the hard drive is not. It only came with a 30 day warranty, I think.

---

### Post by quimkaos on 2009-10-24
yep the questions were for you... 
the format will try to clear the bad sectors, and the one thing that can go bad here is that it can fail, especially if it's a fisical error (the space between the niddle and the plate disks is less than an hair, any big bump can cause a scratch). if its software related (caused by a forced unmount, for instance, like a system crash or a power failure) the format will probably go with no problem. the one that will make your drive skip the sectors is a check disk and it may behave strangely since every time the niddle try to go thru the sectors it'll jump. it's unnoticeable if they are only a few. and there's no way u can tell wen the drive will fail... i had drives that lasted years with bad sectors and others that failed after few days.

has for the warranty, i don't understand how your laptop can still be under it, but not your drive. plus, for instance, in my country it's illegal to sell new products with a warranty period less the 2 years.

---

### Post by patrickaupperle on 2009-10-24
> **quimkaos said:**
> yep the questions were for you... 
the format will try to clear the bad sectors, and the one thing that can go bad here is that it can fail, especially if it's a fisical error (the space between the niddle and the plate disks is less than an hair, any big bump can cause a scratch). if its software related (caused by a forced unmount, for instance, like a system crash or a power failure) the format will probably go with no problem. the one that will make your drive skip the sectors is a check disk and it may behave strangely since every time the niddle try to go thru the sectors it'll jump. it's unnoticeable if they are only a few. and there's no way u can tell wen the drive will fail... i had drives that lasted years with bad sectors and others that failed after few days.

has for the warranty, i don't understand how your laptop can still be under it, but not your drive. plus, for instance, in my country it's illegal to sell new products with a warranty period less the 2 years.

The hard drive that came with the laptop is still under warranty. The thing is, that hard drive still works fine. This is a second, new, hard drive that I bought so that I would not have to worry about the whole dual booting thing. I was actually worried it was going to be a difficult process at the time. I also wanted to leave windows it's full 80GB. Now, the new hard drive, which dell won't cover under the warranty because they did not sell it to me, is failing. I believe there is no such limit on warranty here in the US, but maybe I will look into it.  So, you are saying that these small freezes will stop if I use the low level format tool?

---

### Post by patrickaupperle on 2009-10-24
Well, I just ordered a new HD. I did so because the number of bad sectors increased by 10 and I got another error. 
```
[COLOR="Red"][SIZE="4"]Read Error Rate[/SIZE]
Frequency of errors while reading raw data from the disk. A non-zero value indicates a problem with either the disk surface or read/write heads.[/COLOR]
```
Under the Assessment column for this category it says:
```
[COLOR="Red"]Failing[/COLOR]
```
Then under the Value column there is:
```
[COLOR="Red"]Normalized: 50
Worst: 50
Threshold: 62
Value: 768612578[/COLOR]
```

I think this means that it is basically dead. Thank you all and please correct me if I am wrong.

---

### Post by patrickaupperle on 2009-10-25
The read error rate came back down :confused:. How does this happen? What does it mean? Also, it says that my HD "has many bad sectors", instead of what it said for a while ("Hard Drive Failure imminent" or someting like that.) What does all this mean?

---

### Post by WolfRage on 2009-10-27
It means the tool is doing it's job. As stated before manufacturing tools can be sort of magical when it comes to repair. SO overall the outlook for the drive has improved, continue with the low level format and hope for the best. But you should also know that this could be a mirage. 
I mean that the tool could be either repairing the sectors or masking the bad sectors by rewriteing the flow of the drive around the bad sectors. Thus less bad sectors are detected after each repair, but at the same time the drive is lossing capacity as more sectors are written out of the flow.

---

