---
title: "Getting Error 13: Invalid or unsupported executable format"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by avngrboy on 2009-09-20
hope this is in the right area.
Getting Error 13: Invalid or unsupported executable format




I am having some problems. I had vista and ubuntu on a 160 hd and everything worked great so I decided to upgrade to a 500gb hd. 

I installed both vista and ubuntu but it just isnt the same. I ran good for about a week and now I get an error message(Getting Error 13: Invalid or unsupported executable format) when I try to boot up to windows. 

Any suggestions. I googled and searched here and tried all of the suggestions but it is still doesnt boot up

Thanks

---

### Post by Partyboi2 on 2009-09-21
Hi, maybe your boot sector is corrupted, if you have a vista disk boot to 'Recovery console' and at the prompt type
```
fixboot
```
then 'exit' and see if you can boot Vista.

---

### Post by avngrboy on 2009-09-21
I fI use your method will it erase anything on my drive? Also, Where would I type that?

thanks for the reply.

---

### Post by Partyboi2 on 2009-09-21
Sorry, for Vista the command from the command prompt seems to be
```
 BootRec /FixBoot
```
You will need to boot the Vista cd and choose the option "Command Prompt"

You can also try "Startup Repair" from the Vista cd and see if that fixes it.
[http://windowshelp.microsoft.com/Windows/en-US/Help/5c59f8c1-b0d1-4f1a-af55-74f3922f3f351033.mspx](http://windowshelp.microsoft.com/Windows/en-US/Help/5c59f8c1-b0d1-4f1a-af55-74f3922f3f351033.mspx)

---

### Post by avngrboy on 2009-09-21
I'll try that. But just want to make sure, will it erase any of my info?

Thanks

---

### Post by avngrboy on 2009-09-21
Just tried it and it still doesnt let me boot into Vista. It gives me the same Error 13.

---

