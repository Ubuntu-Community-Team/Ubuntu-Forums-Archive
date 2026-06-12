---
title: "Mouse back button not working in Intrepid"
date: 2008-11-13
forum: General Help
---

### Post by pijiu on 2008-11-13
I'm running intrepid and having trouble getting my back/forward buttons working. I had a look on the forums and could only find info regarding hardy.

I'm using a Microsoft Laser Mouse 6000 v1.

If someone could point me in the right direction so I can remap my mouse I would be grateful. I had a look on the wiki and found something about xinput but didn't understand what exactly it meant or how to edit it.

---

### Post by pijiu on 2008-11-13
Alright I was playing about with xinput and ended up with no buttons working at all now on my mouse. Sometimes I can get the right button to be left-click and at one point I got it to be right-click but that was a short-lived victory.

I'm really stuck for ideas, how do I work out which button is which and how do I assign it the proper function :/

---

### Post by pijiu on 2008-11-13
```
"Microsoft Corporation Microsoft ? Laser Mouse 6000"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

Also, how come it says I have 32 buttons? :o

---

### Post by oo22 on 2008-11-18
I actually have a very similar problem.  I use a Logitech Mx510 (Wired mouse) and have never really run into problems with my forward and back buttons before (Until Intrepid)..

Now the buttons don't even show up when I run 'xev'!  I googled around for a solution but everything assumes that you can see the buttons in xev.

---

### Post by oo22 on 2008-11-19
I have solved my problem! (Though it seemed to have been very specific).. I use a Mac Pro at work which I have hijacked with Ubuntu.. at any rate I guess while Ubuntu was getting installed it though it was a notebook and installed "mouseemu" which totally screwed up my mouse handling.

So basically just un-installing mouseemu fixed my problem! Though, I did loose keyboard and mouse control immediately after un-install.. Restart X and all my mouse buttons work fine.

---

