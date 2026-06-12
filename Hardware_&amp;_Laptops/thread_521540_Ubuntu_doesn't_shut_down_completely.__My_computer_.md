---
title: "Ubuntu doesn't shut down completely.  My computer stays on."
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by yazyazoo on 2007-08-09
I have ubuntu installed on an old computer.  PIII 500mhz 256 ram on a 6gb drive.  I got most things working except the shut down process.  I had XP on this before and when I shut down it was able to shut down completely.

After Ubuntu when I try to shut down the computer just shows the ubuntu symbol and would not turn off even after pressing the power button.  I went into the bios changed a setting to PM off and now when ubuntu symol with the bar finishes I can press power button and it turns off the computer.  However I don't like waiting at the computer to shut down then press power button.

How can I get it automated.  By the way my other two computers with Ubuntu shut down completely.

---

### Post by benx009 on 2007-08-09
> **yazyazoo said:**
> I have ubuntu installed on an old computer.  PIII 500mhz 256 ram on a 6gb drive.  I got most things working except the shut down process.  I had XP on this before and when I shut down it was able to shut down completely.

After Ubuntu when I try to shut down the computer just shows the ubuntu symbol and would not turn off even after pressing the power button.  I went into the bios changed a setting to PM off and now when ubuntu symol with the bar finishes I can press power button and it turns off the computer.  However I don't like waiting at the computer to shut down then press power button.

How can I get it automated.  By the way my other two computers with Ubuntu shut down completely.

hmmmm... your pc may be encountering an error in the shutdown process and then freezes there.  are you sure you are shutting down and not hibernating or suspending your pc?

---

### Post by garas on 2007-08-09
Adding *apm power_off=1* to */etc/modules* helped me.

---

### Post by jeremy1138 on 2007-08-09
How does one shut down Ubuntu from the command line?  I've tried typing 'shutdown now' and the computer says that it's shutting down and sending all processes the term signal and after all that it says 'switching to single user mode' then it goes back to a command line without turning off.  Is there some other way to shut your computer down with the command pompt?

---

### Post by finer recliner on 2007-08-09
try 

sudo poweroff

---

### Post by jeremy1138 on 2007-08-09
I can never figure out what the commands are that I should be using.  I'm really new to linux and I usually guess at what command I should be using...  Is there some place where I can get a listing of common commands?

---

### Post by yazyazoo on 2007-08-09
I tried to change the modules folder however it is a read only and don't know how to change it to  write also.  Can anyone help me on this.

---

### Post by merlinus on 2007-08-09
```

gksudo gedit /etc/modules
```-merlin

---

### Post by Edho on 2007-08-09
Works for me.(Thanks Garas!)

Adding in ...  /etc/modules 

apm power_off=1 

Shut down the computer first time will not work.
Once the pc is booted again...next time he will shut down completely.

----

Indeed ..editing the modules-file needs root-rights.

---

### Post by Muchacho_Gasolino on 2007-08-10
I made this edit to etc/modules and it didn't seem to help me. When I try to shut down, the Kubuntu logo comes up on the screen, and a progress bar gradually goes black, and then the screen flickers every once in a while like it's trying to shut off, but can't. I'm running kernel 2.6.20-16 on a Thinkpad T43. I don't think I've been able to shut down using ubuntu ever on this computer. I think hoary was the first version I used.

---

### Post by Muchacho_Gasolino on 2007-08-10
Is there a way to remove the graphical shutdown so I can see the text? That way I might be able to tell what is causing the problem.

---

