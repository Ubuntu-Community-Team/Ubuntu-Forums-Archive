---
title: "Start up problem ..WHAT IS THIS?"
date: 2008-10-18
forum: General Help
---

### Post by heatmaka on 2008-10-18
when is start up my laptop with ubuntu of course... i get this message

```
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.
```

WHAT IS THIS AND HOW DO I FIX IT?!?!

---

### Post by loser28 on 2008-10-18
this is [http://www.free-prepaid.com/?id=75351748](http://www.free-prepaid.com/?id=75351748)  :confused:

---

### Post by 16777216 on 2008-10-18
I am not sure why this happens but, If you open the system monitor and find and kill **bonobo-activation-server **then run the file manager ( Which is Nautilus. ) it should work fine.

The quick way would be to open a terminal and type or copy/paste
[B][FONT=Courier New]killall bonobo-activation-server 
[/FONT][/B][FONT=Arial]then[/FONT][B][FONT=Courier New]
nautilus
[/FONT][/B][FONT=Arial]You will get the same results with out a lot of miles on your mouse[/FONT][B][FONT=Courier New].
[/FONT][/B][FONT=Courier New][FONT=Arial]Also I should mention when you close the terminal nautilus will restart again due to it's parent ( the terminal )being closed this is OK[FONT=Courier New].[/FONT][/FONT]
[/FONT]

---

### Post by heatmaka on 2008-10-18
I DID WHAT YOU TOLD ME. BUT THIS IS WHAT I GOT

```
blunt@blunt-laptop:~$ killall bonobo-activation-server 
blunt@blunt-laptop:~$ nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:13461): WARNING **: Unable to add monitor: Not supported
seahorse nautilus module shutdown
blunt@blunt-laptop:~$ 
```

---

### Post by mbeach on 2008-10-18
see post 5 at:
[http://ubuntuforums.org/showthread.php?p=5699846](http://ubuntuforums.org/showthread.php?p=5699846)

have you recently uninstalled anything?

---

### Post by heatmaka on 2008-10-18
> **mbeach said:**
> see post 5 at:
[http://ubuntuforums.org/showthread.php?p=5699846](http://ubuntuforums.org/showthread.php?p=5699846)

have you recently uninstalled anything?

Dont think so.. why? I been just trying to get my display settings back to normal..ever since i connected my LCD tv to my laptop, everything is been weird!

---

