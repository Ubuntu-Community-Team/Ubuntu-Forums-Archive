---
title: "how to execute a script before printing?"
date: 2008-11-21
forum: Hardware
---

### Post by red_lego_man on 2008-11-21
I have Hardy installed, running cups for printing, everything is tickety-boo.
I have hacked one of those remote control power sockets and can switch on a wall socket with a simple C program.
What I want to do is have it switch on the printer when someone tries to print.  This is where I am stuck.

How can I modify or fudge my current printer setup to run a script as the first thing it does before sending the print job to the printer?  I've looked at filters and all sorts of things, but cups seems quite complex.
All I want to do is have my script run when a print job is submitted to the printer.
Anyone have any ideas?

Thanks

---

### Post by scoon on 2008-11-21
Hey there, 

I am not at my linux box right now so my response is high level.  If you are printing from CLI and you are using the bash shell, you could just alias the print command like so: 
```
alias printingCommand = 'theScriptYouWantToRun && printingCommand'
```

Often times, distros will alias rm with rm -i to ask the user if they are sure they want to remove whatever it is they are trying to remove.  The same kind of idea applies here.

Hope this helps.

---

### Post by red_lego_man on 2008-11-21
> **scoon said:**
> Hey there, 

I am not at my linux box right now so my response is high level.  If you are printing from CLI and you are using the bash shell, you could just alias the print command like so: 

Hope this helps.

Not really, as that doesn't cover prints coming from other hosts via samba for example, or for local prints from applications like firefox or openoffice.  Thanks anyway.

---

### Post by srilyk on 2008-11-21
I'm not 100% sure on how cups works, but I know with most things you can rebind and use aliases, blah blah blah.

I don't know for sure if it's possible, but I would suggest figuring out what type of file is sent to cups, and then writing some type of script to recieve the file, turn on the socket, then write it to cups.

Good luck with the hunt!

---

