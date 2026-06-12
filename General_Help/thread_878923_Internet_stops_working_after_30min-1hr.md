---
title: "Internet stops working after 30min-1hr"
date: 2008-08-03
forum: General Help
---

### Post by zachhill91 on 2008-08-03
I boot up and my wireless card works fine for a while but after a little while the internet just quits, no warnings or nothing.

Any idea why this may be happening?

---

### Post by rEbyTer on 2008-08-03
What do you mean with
> the internet just quits

Your network connection stops working ?

---

### Post by zachhill91 on 2008-08-03
No the connection is fine, I can run for days with other computers and other OSes on this computer.

I did sudo lspci in the terminal and this was the result.
[http://paste.ubuntu.com/33686/](http://paste.ubuntu.com/33686/)

---

### Post by rEbyTer on 2008-08-03
I mean when > the internet quits you can ping google.com ?
In other words, is your ubuntu computer disconnecting without reason from your network?

---

### Post by jebova2301 on 2008-09-09
my computer does the same thing. the wireless works for a short while, and then just quits. my other computers connect fine even when the laptop does that. i havent tried pinging google, but i will tonight after classes and see what i get. i think it is just the ubuntu laptop disconnecting me though. after i turn off the computer and reboot, i can use the internet fine again for a while. it doesnt have this problem when i use my windows boot side. only in ubuntu. i am running 32 bit gutsy(7.10) if that helps at all

thanks in advance

--------------------------
edit

it still shows me connected to the network, and shows that i have connection, but pidgin/amsn/firefox all are unable to connect.

---

### Post by Zorael on 2008-09-09
Try running **route** in a terminal when it's borked and post what it says.

---

### Post by jebova2301 on 2008-09-18
sorry it took me so long to get this up. been really busy with school.

brandon@brandon-lappy:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
brandon@brandon-lappy:~$ ping [http://www.google.com](http://www.google.com)
ping: unknown host [http://www.google.com](http://www.google.com)
brandon@brandon-lappy:~$

---

### Post by mb_webguy on 2008-09-18
When the connection goes down, does "sudo /etc/init.d/networking restart" bring it back up?

If so, as a workaround, I *think* that if you put the following script in /etc/network/if-down.d/ that it will automatically restart networking any time it goes down.```
#!/bin.bash
/etc/init.d/networking restart
```

EDIT:  To do this, type "gksu gedit" in the terminal.  This will open gedit with root privileges.  Copy and paste the above code into the file, then save it as something like /etc/network/if-down.d/restart_networking.  Now exit gedit, and in the terminal type "sudo chmod 755 /etc/network/if-down.d/restart_networking" to make it executable.

Again, I'm not entirely sure this will work.  On the other hand, I'm almost entirely sure it won't hurt to try it.  If it doesn't work, simply type "sudo rm /etc/network/if-down.d/restart_networking" to remove the script.

---

### Post by jebova2301 on 2008-09-18
well...im on it right now, and just waiting for it to go dead. as soon as it does, i will try that code, and hopefully it will work.

this used to happen to me before, but i screwed up a system file, and had to use the windows partition to get my unsaved data. needless to say, i just reinstalled it, and that fixed the problem. but that is a lot of work for one thing. hopefully this works. if not, thanks anyway. as you said, it cant hurt.

---

### Post by mb_webguy on 2008-09-18
By the way, if you add this script after your network connection is dropped, it may not work immediately, since I think the scripts in /etc/network/if-down.d/ only run when the network connection first goes down.  So type "sudo /etc/init.d/networking restart" to manually restart networking, and after that the script should take care of it automatically.

---

### Post by jebova2301 on 2008-09-19
ok...i had tried what you stated earlier, and couldnt get it to reconnect. i will try what you just posted as soon as it goes down again.

thanks for trying to solve it. this is so much nicer than with windows. 24876958357235648957495825798245645 solutions to one problem, and no one knows what they are talking about. at least here, you all seem to have a pretty firm grasp on all of it.

---

### Post by Interpreter on 2008-09-19
I blame the lack of coffee, but what exactly was the problem other than the intertubes dying on you?

Could you also provide the route text while it's not borked?

---

### Post by jebova2301 on 2008-09-19
actually,those scripts may have done the trick. i just dont think i was patient enough. i restarted my computer last night, and then left it on for about 6 hours. internet never went down.

thanks for the help guys.

---

### Post by jebova2301 on 2008-11-25
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0


thats while it isnt borked...it still messes up. im beginning to think it is something with the encryption. if i look at the networks as i walk around, i can see new ones pop in, and others go out of range. any ideas?

---

