---
title: "where is my audio device?"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by jjf on 2006-12-19
It ought to be so simple.  I need to practice a song for a friend's wedding, and I just want a program that will mimic a keyboard so I can bang out a few simple pitches.  

So I find a couple likely candidates, the most straightforward is vkeybd (doc here:
[http://www.die.net/doc/linux/man/man1/vkeybd.1.html](http://www.die.net/doc/linux/man/man1/vkeybd.1.html)
)

The problem is that when I try to run it, I get this error message:

```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ERROR: can't open sequencer device
```

So it sounds like the program doesn't know where to find my sound device.  Ubuntu's Device Manager is no help.  I can see my sound card, but there are 10 entries under it, and none of their paths seem to work when I feed it as a --seqdev argument.  

When I do feed any sort of path to a --seqdev argument, I get this:

```
ERROR: can't open sequencer device '/dev/snd'

```

Any help would be greatly appreciated.  Thanks.

---

### Post by xyz on 2006-12-19
Just a thought...
"vkeybd" seems to need the following dependencies:
> libasound2(>1.0.9)
libc (>=2.3.4-1)
libx11-6
tcl8.4 (>=8.4.5)
tk8 (>=8.4.5)
Did you install them and how did you install vkeybd?

---

### Post by xyz on 2006-12-19
Just to give it a try, I downloaded it:
```
sudo aptitude install vkeybd && sudo aptitude update
```
and it does not work so far....
You may also be interested in:
[HowToVirtualKeyboardKeymapping]("https://help.ubuntu.com/community/HowToVirtualKeyboardKeymapping")

---

### Post by jjf on 2006-12-19
Thanks for looking into this.

I installed it with synaptic, so all the dependencies should have been taken care of.

Ok, some googling turns this up:

> **Virtual Keyboard**

This program is originally for AWE32/64 driver on OSS/Free, but it works now on ALSA, too. Start the program with --device alsa option. Then, connect this client to any ALSA port by aconnect utility, for example,

% aconnect 128:0 65:0

Alternatively, you can use --addr 65:0 option to connect directly from vkeybd.


```
vkeybd --device alsa --addr 65:0
```
 does not work.  Can anybody tell me what args I ought to use?  I guess I'd need to know the ALSA device address in a format like xx : x.  The Device Manager is no help.  I can look at my "ALSA Playback Device," but I don't see any "address" (PCI address?) formatted like xx : x.

---

### Post by jjf on 2006-12-19
Ah, more clues.  From the docs:

>        --addr destination
              Set  ALSA  client and port numbers to be connected.  If argument
              begins with 's' or 'S', the port is opened as subscription port,
              and  events are sent to all connected subscribers.  The port can
              be connected to other ports via aconnect(1).  Otherwise,  vkeybd
              connects directly to the specified port.  The argument must be a
              form like client : port or client.port, where client and port  are
              index  numbers  listed  in /proc/asound/seq/clients.  Default is
              's'.

So --addr xx : x is not a PCI device address, it is a "client (something)" and a "port (something)."  I don't know what that means, but I do know that I want sound to come out of my speakers when I push buttons.  Can anybody tell me what argument to use, or where I might look to find this?  (I have a /proc/asound/seq directory, but there is no ./clients file inside it.)  Thanks.

---

### Post by jjf on 2006-12-19
More progress.  From another thread in these forums, I discovered that I need to 

```
sudo modprobe snd_seq_oss
```

in order to have a sound sequencer (whatever that is).  Now I can start vkeybd and press keys without throwing any errors.  But I hear nothing.  My sound device works otherwise (I can listen to music in Rhythmbox), but no sound from vkeybd.

My guess is that I need a way to tell vkeybd to output to my sound card or speakers.  Help?

---

### Post by jjf on 2006-12-19
Good lord this is maddening.  :mad:  

I've held out for a while now, but...

<whiny_newbie>I bet within 20 minutes I could have found 5 Windows freeware/shareware programs that do exactly what I'm looking for.  All of them would have .exe install files and work right out of box without requiring me to modprobe this or aconnect that.  I don't want a crash course on sound card architecture and driver design, I just want my computer to beep when I push a &$*#^ button.</whiny_newbie>  

](*,)

---

### Post by JNik on 2007-12-10
I just installed virtual keyboard v0.1.17 and I ran into the same problem. The application runs without any problems but no sound comes out when a key is pressed.

---

### Post by bengoza on 2007-12-13
I'm having they same problem you are. No sound comes out when I press the buttons. What do we have to do?

---

