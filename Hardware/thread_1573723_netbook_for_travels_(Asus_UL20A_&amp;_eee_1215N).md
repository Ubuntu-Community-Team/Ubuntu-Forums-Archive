---
title: "netbook for travels (Asus UL20A &amp; eee 1215N)"
date: 2010-09-13
forum: Hardware
---

### Post by jimmyxx on 2010-09-13
Hi all,

I'm looking for a netbook/laptop 11" - 12.6" to take traveling for 6 months. Looking for something with decent battery life - 2gb ram minimum and preferably dual core. It will be used primarily for programming while I'm away, but will also be used for browing travel snaps / videos, emailing etc.

The two I'm currently looking at are: [Asus UL20A]("http://www.geekwithlaptop.com/asus-ul20a-notebook") and the [eee 1215N]("http://notebooks.com/2010/07/03/asus-eee-pc-1215n-updated-specs/").

A big reason I'm thinking about the UL20A is due to it's great battery life (around 8 hours) compared to the ~5 hours of the 1215N. Anyone have experiences with this laptop?

The 1215N looks like an awesome piece of tech but my main concern with the 1215N is it's a little too bleeding edge for ubuntu with it's ION2 stuff. What little I've found searching "1215N ubuntu" looks like people are having difficulties with the networking but more importantly it's gpu switching. Does anyone have a 1215N, if so how does it run?

They are both the roughly the same price. Does anyone have any other suggestions I could look at?

Thanks

---

### Post by omniuni on 2010-09-13
Hey,

I don't have experiences with those machines, but I have an MSI with the Athlon Neo, and it has worked out really well. There are some HP sub-notebooks with similar specs, including a Neo X2, and the Radeon HD graphics. The Radeon is well supported under Linux, and AMD is moving development to the Open Source driver, which is a nice change from the nVidia way of doing things. Added bonus is that the Neo runs MUCH cooler than either the Atom, or the Core2. If you're looking for something speedy, with decent battery life, and easy to install on, I think one of those might be your best bet.

---

### Post by emigdio on 2010-09-13
I just got my brand new 1215n from ExcaliburPC here in US. Of course I bought it thinking in ubuntu, previously I had a 1201N with no issues, everything was working fine. Now for 1215n is another story, everything works except for the NVIDIA GPU, Intel accelerated graphics works out of the box, but I couldn't make it to work for NVIDIA. First I tried 10.04 and turn on drivers manually but when I changed to CLI (disabling gdm) there was no video so I couldn't do it, I imagine the kernel was too old. Then I tried with 10.10 beta. Here the kernel seems better since I could go to command line and disable the nouveau drivers, and then install manually Nvidia drivers. No luck. I couldn't enter to the X server. A common error saying that no monitor was found. I tried several hints shown in the web but at the moment I can't.
Of course with Intel card working you can get at least Compiz working but very basic stuff.

...and I'm still searching if anybody has found a solution

---

### Post by jimmyxx on 2010-09-14
Hey guys, thanks for your input.

I've ruled the 1215N out now - I know it's probably the best piece of kit but seems like it's just going to be a big headache which is the last thing I want while travelling with limited internet access.

I'm now down to the Asus UL20A and the Acer 1810tz both seem very similar & both seem quite linux friendly.

Will do a little more research tonight!

---

### Post by jimmyxx on 2010-09-15
Hey guys - I ordered the UL20A instead of the Acer 1810tz

Reasons were: 

[LIST=1]
[*]12.1" display rather than 11.6
[*]1280x800 resolution (more vertical height)
[*]Looks realllly nice (this was the main factor lol)
[/LIST]

Unfortunately the model I ordered has an SU2300 dual core processor which is not quite as quick as the Acer's. Other thing is there is no HDMI - this doesn't bothered me too much though. 

I'll post when its arrived and I've got ubuntu running on it!

---

### Post by ssdlucas on 2010-10-19
Interested in your post. I was also trying to choose between the 1215n and ul20a. Prefer the look of the ul20a from what I've seen on youtube, have been unable to find any in the stores. But appear to be a higher quality finish, although 1215n looks and feels good.

What do you think of the UL20a? Is the su2300 processor OK?. Budget won't stretch to the su7300.
[B]
[/B]

---

### Post by jimmyxx on 2010-10-21
Hey ssdlucas,

Yeah love my UL20A - build quality is *great* and it looks a lot more expensive than it was! Battery life is very good - I've not timed it but I reckon i get 6/7+ hours use. SU2300 seems nippy so far, can use google earth smoothly, full screen 1080 youtube vids, javascript tech demos etc. I've not done any real work on it yet - but I'll be in a better position to review it soon as I'm setting travelling for 6 months on Saturday with my UL20A in my bag! ^_^

I installed 64bit ubuntu 10.04 on it when it arrived which I've since upgraded to 10.10. Installation & upgrade was perfect - all worked out of the box.

Couple of gotchas:

[LIST=1]
[*]Couldn't get CPU frequency scaling working :(
[*]You have tweak a line in a settings file to get the brightness keyboard shortcut working
[*]Wireless has recently started being a slightly intermittent - I *think* this is since I upgraded to ubuntu 10.10
[/LIST]

The reason I didn't go for the 1215N is because heard it wasn't ubuntu-friendly. Didn't seem like I could find a single person who had it working properly.

Hope this helps! :KS


Edit: I can't play my 1080i AVCHD vids smootly on it (which play fine on the stock windows 7 install) but I think this is more an issue with linux AVCHD support rather than than the UL20A

---

### Post by henrywm on 2010-10-21
Who is a good vendor for a netbook with Ubuntu already pre-installed (so that I do not even need to pay for Windows)?

---

