---
title: "How to get Hauppauge Nova-T 909 remote working"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by SFAOK on 2008-02-21
Configuring LIRC and Nova 909

I picked up a Hauppage Nova-T DVB card (909 model) so that I could use my Ubuntu box as a TV in the bedroom, but I had some difficulty getting the remote to work.

I have a fairly ordinary Ubuntu Gutsy install and am using Kaffeine to watch TV. Initially, some of the remote's buttons would work but at a 'Gnome' level - the volume buttons brought up an on-screen display, the "OK" button worked as enter, the Power button brought up the Log Off/Power off panel. I believe it's set up as a keyboard of sorts but Channel Up and Down didn't work this way. Not ideal.

I'm posting this guide because I hope it will help someone else who experiences these problems (in retrospec, I wish I'd seen this guide earlier: [http://ubuntuforums.org/showthread.php?p=1061031](http://ubuntuforums.org/showthread.php?p=1061031) which I found after posting this thread - but I've got some additional info below (and I'm not sure if it would've solved my biggest problem) so I'll keep it up. If you're using Kubuntu, you may wish to try that guide instead!)

This guide is with my hardware and using Kaffeine for TV in mind but hopefully you can apply the lessons here to your card/program/remote - I'll try and offer agnostic advice where I can.

[SIZE="2"]**0. Static device**[/SIZE]

This step can be done first or last - but it's probably better to try it first, otherwise you'll have to make changes once your remote is working. However, if you have trouble getting this first bit to work, you can follow the rest of this guide to see if you can at least get your remote to work. 

When booting up, Ubuntu assigns the remote sensor to /dev/input/eventN where N is a number that is not always the same on every reboot. You can prevent this with dbus magic that creates a symlink to whatever /dev/input/event the sensor is assigned. Sound difficult? It's not, [http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php) walks you through (scroll down to the "Make the LIRC Device Static" entry).

Two points to note: I did read somewhere that the parker guide can be problematic in certain cicrumnstances; I *think* when there are two TV cards in your box - but can't confirm. Just a warning that YMMV!

Secondly, when the guide walks you through finding the vendor ID with udevinfo, there may be a couple of suitable entries for the vendor ID in the output - I used the first one (I think it matched the one in the guide).

[SIZE="2"]**1. Install LIRC **[/SIZE]

Open Synaptic and search for LIRC - you only need to install the lirc package. Alternatively, 

```
sudo apt-get update && sudo apt-get install lirc 
```

should do the trick.

If prompted to select a remote, choose the option that says "My remote's not listed" (or similar).

[SIZE="2"]**2. LIRC Config**[/SIZE]

Next, the lirc configuration files, which can be found here under the LIRC Config section: [http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php)

Grab the hardware.conf and lircd.conf files and stick them in /etc/lirc using sudo e.g. 

```
sudo cp lircd.conf /etc/lirc/ 
```

Note the author's note regarding an alternative conf file for newer remotes. In my case, I needed the alternate file.

You'll also need to put the device in /dev/input/event that relates to the sensor into the hardware.conf file. Change the LIRCD_ARGS line to read 

```
LIRCD_ARGS="--driver=/dev/input"
```

and the DEVICE line to read:

```
DEVICE="/dev/input/ENTRY" 
```

where ENTRY is the corresponding entry in /dev/input/ that relates to the sensor. If you followed step 0 succesfully, this will be /dev/input/irremote. 

If you didn't do that step, you'll need the output from cat /proc/bus/input/devices - the remote sensor should be listed and you're interested in the Sysfs line which will indiciate which entry in /dev/input to use e.g. if the line reads Sysfs=/class/input/input3, you'll need to put event3 as ENTRY.

[SIZE="2"]**3. Testing LIRC**[/SIZE]

Let's see if your remote is working. Open a terminal and check lirc is running - I run 

```
ps -eaf | grep lirc 
```

which should return two entries if it's running. If it's not running, sudo /etc/init.d/lirc start should start the daemon. Now enter irw. The program looks like it hangs the terminal but point your remote at the sensor and start pressing buttons. You should see output such as:
```

0000000080010192 00 ChannelUp hauppauge_nova_t_uk
0000000080010002 00 1 hauppauge_nova_t_uk
0000000080010069 00 Left hauppauge_nova_t_uk
```

If you do, congratulations, your remote is working, but we're not quite done yet... If you don't see text like the above, post what you tried and what output you got and I (or someone else) may be able to help.

[SIZE="2"]**4. .lircrc**[/SIZE]

Now your remote is working, let's get it doing exciting things like changing channels in Kaffeine/whatever you're using to watch TV. This requires setting up an .lircrc file (or files) in your home directory.

I'm only going to cover the basics here - all sorts of magic can be performed with the right .lircrc file but there are other guides out there that cover that already.

Create a file called .lircrc in your home directory and open with your text editor of choice. We create entries here that map buttons to actions. An example of the syntax:

```
begin
  prog = XXX
  button = YYY
  config = ZZZ
end
```

This basically says "If key YYY is pressed, pass action ZZZ to appliction XXX." So in Kaffeine's case, we just need to say "If channel up is pressed, tell Kaffiene to change the channel" right?

Sadly not; at least, not in a way that I could manage. Some programs can receive events from lirc, so it's possible to set up your remote buttons to pass the right commands (e.g. keyboard combinations that perform the actions in your application of choice) to those applications. If you're not using Kaffeine, go and check if what you do use knows how to play with LIRC and save yourself time and hassle! Example rc files may exist that you can copy to the relevant directory and use right away.

According to the Kaffeine FAQ, Kaffeine does support LIRC using "kaffeine.profile.xml" and the klirc module of KDE 3.2. I couldn't see this package in the Ubuntu repositories, though I didn't look very hard (there was a kdelirc package that may supercede klirc - I'm not sure!). Running a Gnome desktop, I wanted to avoid installing more KDE libraries if possible (and I found out this other way to get things working first so stuck with this).

[SIZE="2"]**5. irexec**[/SIZE]

So I couldn't control KDE from my .lircrc file. The solution was to have a program called irexec running and use DCOP calls to pass messages to Kaffeine. Example:

```
begin
  prog = irexec
  button = ChannelUp
  config = dcop kaffeine KaffeineIface next
end
```

So instead of calling kaffeine as you may expect, irexec is called instead. This then makes a DCOP call to Kaffeine with an instruction of what to do. So in the above example, it basically means that when Channel Up is pressed, irexec is called which uses DCOP to pass a message to Kaffeine to change the channel. You can go through each of the buttons you'd like to use in Kaffeine and assign them the relevant DCOP command to perform that action.

[SIZE="2"]**6. Power off and other fun**[/SIZE]

Note that while irexec is running it will intercept all remote button presses. For example, the volume and power buttons work without any lirc/irexec magic in Gnome but whilst irexec is running (at least, with my .lircrc file), they will not change the volume/bring up the "log out/power down" prompt like they usually do.

This was a problem for me because a. I wanted to switch the computer off with the remote (I don't want to get out of bed to turn the computer off!) and b. I couldn't figure out how to bring up the Log Off/Power Off prompt through irexec.

My solution was to only start irexec when Kaffeine was started and kill it once the Power button was pressed. So when I'm watching TV, I press the power button once (and that kills irexec - which also means I can't change channels any more), then press it again (which will bring up the logoff/power off prompt).

To do all this, first I put a little script in my home directory with the following:
```

killall irexec
irexec -d
kaffeine
```

This kills all irexecs (having two running at the same time can cause problems), then starts irexec in daemon mode (basically shunts it to a background process), then starts Kaffeine. Put the above into a text file somewhere suitable then make it executable (chmod u+x scriptname). Update your Kaffeine shortcut to run this script instead of just loading Kaffeine.

To kill irexec when the power button is pressed, add this to your .lircrc file:

```
begin
  prog = irexec
  button = Power
  config = killall irexec
end
```

This kills irexec when the power button is pressed and brings back the "Gnome level" control from the remote - volume buttons, power button etc.

You don't have to do all this - if you're happy with irexec being loaded when you log in, add it to your session profile (System > Preferences > Sessions > Add).

The .lirc file I use looks like:

```
begin
  prog = irexec
  button = ChannelUp
  config = dcop kaffeine KaffeineIface next
end

begin
  prog = irexec
  button = ChannelDown
  config = dcop kaffeine KaffeineIface previous
end

begin
  prog = irexec
  button = Power
  config = killall irexec
end
```

Just the basics, but it works for me!

[SIZE="2"]**7. Wrap up**[/SIZE]

So there we go, we made a few hacks along the way (and I'd love to hear any neater ways of doing anything I've mentioned here) but we're now able to change channels whilst watching TV through Kaffeine, as well as power off the computer. 

I'll do my best to answer any questions so do post if you have any. Similarly, if you found this useful, please let me know; as it is, I figure that this guide has an audience of two people but it'd make all the typing worth it if I knew it was helping more people than that! ;)

The resources that helped me piece all this together:

Kaffeine dcop call examples: [http://www.netikka.net/holm/holm/linux/lircrc](http://www.netikka.net/holm/holm/linux/lircrc)
This provided a big "Aha!" moment for me: [http://ubuntuforums.org/archive/index.php/t-240227.html](http://ubuntuforums.org/archive/index.php/t-240227.html)
This also helped: [http://www.hauppauge.co.uk/board/showthread.php?t=7085](http://www.hauppauge.co.uk/board/showthread.php?t=7085)
Mr Parker's rather brilliant MythTV guide: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
Some good tips on configuring lirc: [http://www.g-loaded.eu/2006/01/10/how-to-configure-and-use-lirc/](http://www.g-loaded.eu/2006/01/10/how-to-configure-and-use-lirc/)

Thanks!

---

### Post by patrickfromspain on 2008-02-26
Great guide! Has been very helpful to me.

Anyway, maybe you want to look into irkick, it comes with the kdelirc package. It's great for configuring the remote control to use it with amarok or kaffeine.

---

### Post by SFAOK on 2008-03-08
Yep, I'd definitely recommend irkick if using KDE. It acts as a replacement to irexec in my example above (plus, I think it has configuration tools too). However, I decided to use irexec as it was already installed and I'm a gnome user so wanted to avoid loading yet more KDE modules - after loading Kaffeine, I may not be saving that much but oh well :)

---

