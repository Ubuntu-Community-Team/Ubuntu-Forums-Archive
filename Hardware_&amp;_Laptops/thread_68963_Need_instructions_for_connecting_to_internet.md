---
title: "Need instructions for connecting to internet"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by wpshooter on 2005-09-24
O.K., I discovered that my initial try to get Ubuntu was not working because the 3 laptop computers I was trying to install on had only 64mb of memory.

I have now gotten the **live CD ** O/S installed on one of my home computers (which has 512mb of memory).

Now I need instructions on setting up the dialup connection to my ISP.

I know all of the normal parameters that are needed to set this up on a windows system.

Will I need my ISP server IP address as opposed to just their name ?

When I go into the section that relates to the modem setup, it says something about it not being activated.  I got it activated but I am not sure about the parameters that I used in doing so.

Is there something in Ubuntu that is comparable to the diagnostic that is run on the modem in Windows to test it's dialing capabilities ?

Are there instructions for this built into the HELP system ?

Thanks.

---

### Post by adwait on 2005-09-24
Try this command,
```

sudo pppconf

```

It will ask you for all the necessary info. If you want a graphical dialer, try kppp. You can download and install it using the command
```

sudo apt-get install kppp

```

---

### Post by wpshooter on 2005-09-25
[QUOTE=adwait]Try this command,
```

sudo pppconf

```

It will ask you for all the necessary info. If you want a graphical dialer, try kppp. You can download and install it using the command
```

sudo apt-get install kppp

```[/QUOTE]
 O.K. I tried the top command "sudo pppconfig" & put in what I thought were the correct parameters.  Once I have done this how do I dialup the ISP ?

I think all of that was basically the same thing that I did before when trying to activate the modem.  Is it possible that for some reason that the O/S is not recognizing my modem.  When I finished the activatation process before, it came back with a message basically saying that it can NOT find the modem and to check to see that the modem is hooked up correctly.  I know it is, because it works fine in Windows.  I can see it in the Ubuntu device manager.

---

### Post by fordfan753 on 2005-09-25
Have you got the ltmodem (I think) package installed?
Some modems are referred to as WinModems, and will only work on Windows. Others will work natively.

---

### Post by wpshooter on 2005-09-25
[QUOTE=fordfan753]Have you got the ltmodem (I think) package installed?
Some modems are referred to as WinModems, and will only work on Windows. Others will work natively.[/QUOTE]
 The modem is a U.S. Robotics/3com 56k internal performance pro **hardware** modem - model 5610.

As far as "I Think", I have not loaded anything unless it was loaded by the live CD.  Why would I have to install anything else just to get my modem to work ?

---

### Post by fordfan753 on 2005-09-27
Linux support for modems is a little grafted on, most people that use linux these days have an "always on" connection, so I guess not as much work goes into modems. *ALSO* a lot of modems use Windows drivers, that are not compatible with linux, this is why some modems work and others don't.

---

### Post by Mustard on 2005-09-27
> O.K. I tried the top command "sudo pppconfig" & put in what I thought were the correct parameters. Once I have done this how do I dialup the ISP ?

You can do this command in terminal I think....

```
sudo pon provider_name
```

and use

```
sudo poff
```

to switch it off.  I believe 'provider_name' is already set by the entries you make in pppconfig.  I've taken the basics of this from [Unofficial Ubuntu guide on dialup connections.](http://www.ubuntuguide.org/#configuredialupconnections)

When you get online try

```
sudo apt-get install gnome-ppp
```

...if you are running gnome.  I find gnome-ppp integrates well into the desktop and also has a handy little log output function that the eternally curious will enjoy watching as it confirms its connection.

You can also set up your wvdial to work using a fairly simple but insecure method by setting up a .wvdial.conf file in your home directory. Typing 'info wvdial' in console will give you a good idea of how to start a simple dial up configuration.  Your password is stored in this file in plain text, so I prefer to set it all up with the password encrypted using pppconfig and then accessing the wvdial config file created by that process using gnome-ppp.  I am pretty sure that sets it all up in a relatively secure way.

---

