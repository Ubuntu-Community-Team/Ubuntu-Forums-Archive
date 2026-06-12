---
title: "Laptop keyboard stopped working after Jaunty install"
date: 2009-05-03
forum: Hardware
---

### Post by gcrussell1 on 2009-05-03
Problem: My Laptop keyboard doesn't work after installing Ubuntu Jaunty 64-bit. This is the case in the Grub Loader, Ubuntu, and Vista Home Premium.

History: Computer has never been used for anything but Vista 32-bit. I installed Jaunty 64-bit a few days ago and the built-in keyboard was working fine (but my old Logitech Cordless Elite was used for the installation). Since then, the laptop's keyboard hasn't registered any touches, and the media keys along the upper strip (not part of the keyboard) don't seem to be registering either. The touchpad works fine - scrolls, taps, etc, but not the keyboard. This is especially problematic because A) my Logitech keyboard is 6 years old and bugs out occasionally so I need the built-in keyboard at those times and B) I don't always have the Logitech plugged in anyway - i.e. away from home.

Specs: Dell Inspiron 4200, T7500, 8400M GT, 3 GB RAM, 250 GB HD w/ approx 85 GB free, any other specs on request.

Needless to say, this is pretty bad, I could really use some help with this one.

---

### Post by Dark_Stang on 2009-05-03
The problem happening during the same time as the OS install seems coincidental.
Can you get into the bios with the built in keyboard?
If not, can you get into the bios with the USB keyboard and reset everything to defaults?
The cable that connects the keyboard to the motherboard may have come loose as well.
Or, maybe dell even put a random shortcut/function key for turning off the keyboard (yes, stupid, but who knows).
And lastly, make sure that num-lock isn't turned on on the laptop.

---

### Post by gcrussell1 on 2009-05-03
It is indeed starting to feel coincidental, but, as many freak incidents like this as I've seen while fiddling with my computer, it still feels pretty unlikely - after all, in six years of owning and tinkering with laptops, I've never had this problem occur. My first thought was to reseat the keyboard's connection, and I've tried several times, but one can never be quite sure with those damn ribbon connectors they use on laptops.

I haven't actually tried accessing the BIOS yet, since I've never known much about them. I doubt that the laptop keyboard will access it, but I could try the USB for the reset thing.

The computer doesn't appear to have a keyboard off button, either.

Lastly, if it were a numlock problem, the keys would register, but do something other than what I expected them to. Instead, the keys aren't registering at all. I lived for three months with the numlock thing on my first laptop because I wasn't savvy enough to figure out the problem (and it was a DTR with an external keyboard - same KB I'm using now...), but it's not that simple this time.

The local computer castle has extra keyboards, I might take it there and test one out to see if it's just the keyboard. I hope to hell it's not a MoBo issue though, I'm off warranty, but just barely.

---

### Post by Dark_Stang on 2009-05-04
I agree with the keyboard ribbon complaints. I don't know how many I've almost ripped dissassembling laptops when I'm trying to gently pull the keyboard off (sony and apple computers are the worst). You may want to try reflashing/updating the BIOS if swapping the keyboard doesn't work for you.

---

### Post by gcrussell1 on 2009-05-04
My ribbon's pretty resilient, but it never pushes in very far, and it always feels like it needs to be seated better, although the last time I took the computer apart (gotta remove the mobo to clean the fan :mad:) it was the same way, and it worked just fine.

I might give the BIOS flash a try. I poked around the BIOS and the only thing that pertained to the keyboard regarded whether numlock or fn sets off the embedded numpad, not that embedded numpads are worth using anyway... If not, it's 5 days til I can go to the computer castle to try swapping keyboards, if they've got one that'll work anyway (there's about half a floor of used, BYO laptop stuff, but it's mostly 2 or more years old...).

---

### Post by gcrussell1 on 2009-05-06
Here's an update: I have updated the bios, completely removed Ubuntu, extended the Vista partition, fixed the master boot record, etc. I suppose this ceases to be an Ubuntu issue here, but it's still possible that someone here can help me, and it did begin as an Ubuntu issue.

Now, the current state of things: The keyboard still doesn't work as it should, but the computer clearly recognizes the button presses on some level. When I have booted up the computer lately (since installing Ubuntu), it beeps at me after the BIOS loads. Tapping any key on the built-in keyboard stops this beeping, which makes it clear that the key-presses are seen by the motherboard. I've already flashed the BIOS, what else can I do to get this keyboard working?

---

### Post by Dark_Stang on 2009-05-07
If it's beeping whenever you turn the computer on, that usually indicates a stuck key or a bad keyboard. I get these every now and then at work, most of the time it's just a stuck key and it takes 10 seconds to fix. Sometimes it's a bad keyboard (usually due to spilling something on it). Have you tried replacing the keyboard yet?

---

### Post by gcrussell1 on 2009-05-08
Dell Diagnostics seems to agree with you on the stuck key thing. I haven't spilled anything on it, and none of the keys are visibly stuck. Any idea what key would have to be stuck to cause the keyboard to not function at all? The other similar posts I've seen on other boards indicate similar problems where the keyboard still gives functional input to the computer, but the key that's stuck (say fn) taints everything else that is pressed.

There may be other issues that Dell Diagnostics didn't see, as well - the next test after the stuck key one was a "press each key in turn" test, and it would read no keys from either keyboard, not even enough to abort the test, so I had to pull a hard reboot.

Incidentally, thanks a lot for all the help, I've posted this issue on several different sites, and you're the only person who's been more than marginally helpful - I've got high hopes of kicking this thing soon, and if not, I can at least get a cheap portable keyboard until I get back Stateside to get the keyboard replaced by Dell - they've got these cool, cheap mat keyboards at my local computer castle that roll up and connect by USB and would be almost as portable as the laptop without an external keyboard at all, so that would get me through the next couple months in manageable, if not ideal fashion.

---

### Post by Dark_Stang on 2009-05-08
Any key that's depressed can cause beeping at the POST screen. If it IS a stuck key, I would think it would be a Ctrl, Alt, Fn, Super (windows), or any other key that doesn't give immediate feedback. I'd just do this to each key on the keyboard.
Push the key down firmly. Wiggle it around a little. Press it several times so you know you're making good contact and the key is being released. Then wiggle it around a little more. This might take a while since the average keyboard has over 85 keys.

---

### Post by gcrussell1 on 2009-05-08
Hmm, I'll give that a try. I had a series of J's on a diagnostic thing, so it might actually be the J key, though I would expect that to register on the OS's and not to preclude the other keys, as I thought that a stuck letter key was overridden by the first key to be pressed after it. Part of the reason I don't think it's one of those keys you mentioned is that they interact with other keystrokes, and unless the stuck key is voiding the whole keyboard (seems to be the case), it would tweak what I typed on the other keyboard, wouldn't it? My plan was to pop all the keys off and then put them back on after looking over the board for any possible problems, which might follow your simpler, faster idea.

What about the possibility that the beeps are a BIOS error code? I've looked around for the beep codes for Inspiron 1420's, but to no avail. It's a series of short, consistent beeps, about four a second, which seems like a potential stuck key problem, but I'd like to know if that might be a BIOS code instead, and if so, what it could mean.

---

### Post by gcrussell1 on 2009-05-08
Ugh, a turn for the weird and possibly very bad: I mentioned before that there was one instance (when booting with the Dell Diagnostics CD in the drive, but not booting into Dell Diagnostics) where it came up with a command prompt (a:) and started spewing out j's like the key was stuck down (it was actually more like "ts}{jjjjjjjjjjjjjjj..."). Well, I just booted up into that same situation with the keyboard disconnected, and the same thing happened - a bunch of j's - with no internal keyboard and no stuck keys on the external one. After the j's piled up too much, the keyboard overload beeps started, and they were definitely different from the bootup beeps. Am I crazy to think that this means my MoBo is the cause of the problem?

I know by now that I should be asking this elsewhere, but in five other forums I haven't gotten a single response in a day and a half, so I'm asking in the only place where I'm actually getting any help. I'm still on warranty, which is good, but I won't be back in the States for 2 more months, and my warranty isn't international, so I'm kinda screwed for official repairs right now.

I guess those mini-USB keyboards are looking pretty good by now... wonder if I could make it to the computer castle before it closes? Nah... tomorrow.

---

### Post by Dark_Stang on 2009-05-08
If you've got the onboard keyboard unhooked and it's still spewing out keystrokes, then your chances are really good that it's the motherboard. Just be glad you're under warranty still.

---

