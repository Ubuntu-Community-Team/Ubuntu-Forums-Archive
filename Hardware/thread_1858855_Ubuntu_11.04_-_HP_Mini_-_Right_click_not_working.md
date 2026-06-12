---
title: "Ubuntu 11.04 - HP Mini - Right click not working"
date: 2011-10-13
forum: Hardware
---

### Post by Ken.B on 2011-10-13
Hi everyone, 

I'm a newbie, as the title says, the right click on my touch pad isn't working. However, the scroll button is functioning.

I've tried the following steps but it says that permission is denied. 

I've typed in

1. sudo su
2. echo option psmouse proto=exps
3. /etc/modprobe.d/psmouse.modprobe

Did I do anything wrong?

> **[B]Re: HP Mini 210 touchpad right click not working**[/B] 			
[B]To get the  trackpad working correctly you need to use the terminal and enter in the  below commands. Make sure you press enter after each command:

[/B]       	**Code:**
 	**sudo su** 
     	**Code:**
 	**echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe** 
     	**Code:**
 	**reboot** 
[B]
Once the computer reboots your trackpad will be able to do left click and drag and right clicking.[/B]
 				[I][B] 					 						Last edited by Sabot; February 13th, 2010 at 03:09 AM.

[/B][/I]

---

### Post by coffeecat on 2011-10-13
> **Ken.B said:**
> Did I do anything wrong?

You used a howto that is ancient in Ubuntu terms and would have referred to a version of Ubuntu that is much older that the one you are using, and may not be appropriate.

Also, if you really did this:

> **Ken.B said:**
> 2. echo option psmouse proto=exps
3. /etc/modprobe.d/psmouse.modprobe

Instead of this:

> **Ken.B said:**
> echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe 

...you would have got an error, but not a permissions one.

So, exactly what was the error and after which command did you get it? Also - post a link to the thread/post you were following. We need to see it in context.

And post the output of this comand:

```
cat /etc/modprobe.d/psmouse.modprobe
```

We need to see if you created that file and, if so, what is in it.

---

### Post by Ken.B on 2011-10-13
[http://ubuntuforums.org/showthread.php?t=1388164&highlight=right+click+-working](http://ubuntuforums.org/showthread.php?t=1388164&highlight=right+click+-working)

This is the thread that I were following.

Now my touchpad is working, do I have to post this into the terminal?

     Code:
     cat /etc/modprobe.d/psmouse.modprobe 

Before I typed this,
> 
2. echo option psmouse proto=exps
3. /etc/modprobe.d/psmouse.modprobe


I did typed this but nothing happened

>  echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe


Thank you very much!

---

### Post by coffeecat on 2011-10-14
> **Ken.B said:**
> 
Now my touchpad is working, do I have to post this into the terminal?

If it's now working, no. My guess is that you simply needed to do a reboot after typing in that code.

If you typed:

```
echo option psmouse proto=exps
/etc/modprobe.d/psmouse.modprobe 
```

On two lines as you have posted it, you would have got some sort of error. But it seems as though you really did type:

```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

```

And that would have created the file /etc/modprobe.d/psmouse.modprobe with the necessary code to make your touchpad work, but probably only on a reboot. When you say "nothing happened", you would have got no feedback from the terminal, but something would have happened. The terminal is a sometimes perplexing environment to work in. Most of the time you get no feedback when a command is executed successfully.

Anyway, glad it's working, and good luck with using your HP Mini!

---

### Post by Ken.B on 2011-10-14
Thanks for your help, coffeecat! :)

---

