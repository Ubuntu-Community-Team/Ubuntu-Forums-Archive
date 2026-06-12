---
title: "Toshiba Tecra 520CDT"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by lucus on 2005-02-08
uh, i am very much a newbie to the linux environment, but i like all the ability to customize.
my problems are these....
1 my sound card doesn't work (how do i go about finding information on how to fix this?)
2 i can't change the screen resolution and the window boxes are too big for my screen sometimes (so i cannot see all the options, or other annoying little problems), also graphics are a little rough looking.
3 i cannot connect to the internet  with my LAN PC card....

if anyone can help i would be very thankful, as i want to learn this new environment, and i like Gnome much better than windows XP even with these few problems.  if this were windows i would know i need a new driver.  but i am not sure just how hardware interacts with a linux environment.

thanks

---

### Post by mendicant on 2005-02-08
Looking here: [http://criggie.dyndns.org/tecra530cdt/](http://criggie.dyndns.org/tecra530cdt/) (via linux-laptop.net), it seems mildly likely that you have one of the ISA cs423x cards, so try:

% sudo xterm 
% # in that xterm:
% modprobe snd-cs4232 
% # or
% modprobe snd-cs4232 isapnp=1
and also try the options given on the above page if that doesn't work.

Screen resolution seems to be 1024x768, and can't go higher.  Is that what you're running?

What's the PC Card you're using?

---

### Post by lucus on 2005-02-08
thanks Mendicant for responding..
i tried what you said, and i was then told that there was no such device...
i just did a bit of research and found that it should be a Yamaha OPL3-SA3 sound card.


my screen resolution is firmly set at 640x480 (as you can see why i am experiencing problems)

my card is a 3comMegahertz 10/100 Lan card... if you need the model number too, i can give you that.  it is a TypeIIx2 or TypeIIIx1 controller

thank you so much for helping me!!

---

### Post by lucus on 2005-02-08
Mendicant your suggestion about modprobe helped me know where to look.
and in doing so, now i have sound working on my computer!!!!!
this makes me really happy because i am listening to a song my good friend recorded on a CD!!!

now only 2 more problems!!!
thank you!!!

p.s. not having to reboot everytime you do something is freaking awesome!!!

---

### Post by mendicant on 2005-02-09
For the screen resolution problem, it sounds like an XF86Config-4 problem.  What are the contents of that file?  Also check the output in /var/log/XFree86.0.log and look for lines beginning with (EE) and maybe (WW).

For the PC Card, does it beep?

---

### Post by lucus on 2005-02-09
ok, the Card does beep when i insert it, and when it is loaded up in the boot up.

there are some WW's
-some stuff about fonts not loading...
-Open APM failed
-System lacks support for changing MTRRs
-oh... CHIPS(0): Probed monitor is 230x170 mm, using Displaysize 800x600mm
-CHIPS(0): Disabling HW Cursor on stretched LCD

 no EE's

i am using a different computer to access the internet (since i don't know how to work that Ethernet card), i have no CD burner or disk drive, so i would have to hand type in the whole XF86Config-4 file.  if you would like me to do that i will gladly, but if i can get the LAN card working, that would be an easier way to put that up here....

---

### Post by mendicant on 2005-02-09
So for the card, there should be two high beeps.  Beep failures are only one high beep, or high beep then low beep.  So do you get the two high beeps, or one of the failures?

Also see:
[http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-2.html](http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-2.html)

---

### Post by lucus on 2005-02-09
i get two high beeps when i plug in the card

when i did
sh -x /etc/pcmcia/network start eth0
near the end of the file it says Ignoring unknown interface eth0=eth0

why would it ignore it?
i am kinda confused

---

### Post by mendicant on 2005-02-09
Ah, so what are the contents of /etc/network/interfaces?  You'll need an entry for eth0
Typically, you'd want:

iface eth0 inet dhcp
# for a dhcp controlled network

or something like

iface eth0 inet static
  address 192.168.0.2
  netmask 255.255.255.0
  broadcast 192.168.0.255
  gateway 192.168.0.1

---

### Post by lucus on 2005-02-09
yeah... wow, mine doesn't have any of that.
it just says map eth0.
actually it says 

#the loopback network interface
auto lo
iface lo inet loopback

#this......(blah blah blah)
mapping hotplug
         script grep
         map eth0

---

### Post by mendicant on 2005-02-09
That looks like a very strange entry.  The mapping stuff usually looks like:

mapping eth0
  script /script_to_determine/a/string_to_output
  map something something something eth0-home
  map something something something eth0-work

iface eth0-work ...

iface eth0-home ...

It's a handy mechanism for changing this, although the Gnome network profile stuff is more 'accessible' for most people.

Anyhow, just put in a correct entry and try it again, and you should be good to go (that is, to work on your X problem :) )

---

### Post by lucus on 2005-02-11
i tried typing in iface, but it said that it didn't exist.  i did read up on that site you suggested, but did not make much progress.  it is pretty frustrating sometimes.
ah, well.
thank you very much for all your input, and helpful advice!

---

### Post by mendicant on 2005-02-11
The iface stuff (you don't want the mapping example right now) should go into /etc/network/interfaces.  Mine looks like:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

In your case, you probably don't want the auto eth0 line (that means that it will be automatically brought up at boot time).

iface is not a command for the command line--it's a command to go into /etc/network/interfaces.  You don't need to look at the pcmcia debugging site.  Your card works and is detected.  You just need a correct /etc/network/interfaces file.  Again, if you use DHCP, you can just use the above lines (minus the auto eth0).  If you have a static IP address, you can use a file like:

auto lo
iface lo inet loopback

iface eth0 inet static
  address 192.168.0.2
  netmask 255.255.255.0
  broadcast 192.168.0.255
  gateway 192.168.0.1

Of course, the exact IP addresses depend on your network.

You can modify /etc/network/interfaces by doing the following:

% sudo cat > /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp
<CTRL-D>

This should change /etc/network/interfaces to use DHCP for eth0.  Once you plug in the card, if the interface doesn't come up automatically (see it via ifconfig eth0), you can just do a

% sudo ifup eth0

---

### Post by lucus on 2005-02-12
[QUOTE=mendicant]The iface stuff (you don't want the mapping example right now) should go into /etc/network/interfaces.  Mine looks like:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
[/QUOTE]

thank you so much!!!
i am typing this from my computer with the newly working Ethernet card!!!!
i am very glad that this works!!
it gives me great hope when it comes to installing a wi-fi card (sometime in the future)
now i face only one more obstacle... the screen resolution problem.
thank you so much for helping me with all these problems.
with this online forum for support, the lack of rebooting, and the lack of blue screens (of death) i found this is be many times less frustrating than the past experiences i have had installing windows.
and i have even had less obstacles to overcome.  i have only had 3, and now i am down to one.
you rock!

---

### Post by mendicant on 2005-02-12
Great!  Good to hear.  Now about your screen resolution problem.  How about you post your /etc/X11/XF86Config-4 and /var/log/XFree86.0.log?

---

### Post by lucus on 2005-02-12
ok here they are... i had to compress the log file, at first i deleted the intro stuff, so none of that is in there.  if you need it i will resend the file compressed
also, i changed the section monitor... display size to 800 600, and it made the ubuntu intro screen way too small, and didn't effect the actual Gnome resolution, so i just recently switched it back to 640 480 in hopes that i could read what the screen says.
but when i had it at 800 600 in the xf86config-4 file the gnome resolution was set at 640 480 as it currently is.  this is why i am perplexed.
your help has been endlessly benificial.
i have not only learned a lot about using gnome, but also bash.
i am excited to type this from my computer!!!

---

### Post by mendicant on 2005-02-12
The chipset says it can do 800x600.  So you can probably just use a Monitor section like:

Section "Monitor"
        Identifier   "Generic Monitor"
        VendorName   "TFT"
        ModelName    "Active Matrix 12.1"
        Option "DPMS"
EndSection

In your "Screen" section, you should change every "640x480" to "800x600".  You can also get rid of all the color depth subsections except for Depth 16 and Depth 24.  If that doesn't work, you'll have to enter something like HorizSync 31.5-38 in the monitor section.

---

### Post by cobbk2001 on 2005-03-20
So how did you get sound working? Most of the setting I have tried don't work - I have one fix that gives feedback from the microphone though.

Toshiba Tecra 8000 - same sound card.

---

### Post by scotty on 2005-04-15
Hi,

I am in the same sound boat as you.  I have an OPL3-SA3 card that ain't being seen by Ubuntu.  What modprobe worked out for you?  I have been all over the forums here.  I see lots of Thank Yous, but no posts of commands to be used.

Thanks,
Scott

---

### Post by lucus on 2005-05-01
modprobe snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530


this is how the sound will start to work ( i think)
i looked for a long time online to find the info i found... because frankly i kinda forgot how i did it.
basically i just added this line in, so that when my computer starts it automatically does this modprobe... and bingo SOUND!!!!!

---

