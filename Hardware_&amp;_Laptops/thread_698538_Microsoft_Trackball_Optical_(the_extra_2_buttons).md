---
title: "Microsoft Trackball Optical (the extra 2 buttons)"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by PiggiePaul on 2008-02-16
Now I know this has been discussed before, but some of the advice is YEARS old, plus last night I followed some advice in a posting about editing the [COLOR="Blue"]xorg.conf[/COLOR] file and totally screwed myself as I lost ALL the buttons, and could not do anything !!!

So, perhaps (as my [COLOR="Blue"]xorg.conf[/COLOR] file) seems a little different in the mouse section to some others in earlier postings, that I'd better ask a-fresh in case a different solution is relevant now with Ubuntu 7.1 Gutsy.

So, I have a Msoft Trackball Optical. Picture here:

[http://www.thepocket.com/page8/pr020901g.gif](http://www.thepocket.com/page8/pr020901g.gif)

It all works perfect and I don't wish to change anything, APART from getting the two extra side buttons to do the (normally default) Forwards/Backwards whilst in Firefox.

At the moment the left "extra" button does nothing at all.
And the right "extra" button does exactly the same as the normal right mouse button.

And (the important bit) Here is my [COLOR="Blue"]xorg.conf[/COLOR] file:


[COLOR="Blue"]Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection[/COLOR]


Any help much appreciated :)

---

### Post by oldsoundguy on 2008-02-16
according to this:

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

you need to change the number 3 to a higher number.

My Logitechs loaded out of the box, so I did not have to make any changes.

---

### Post by Krydahl on 2008-02-16
I have an MS optical trackball, not quite the same model but it does have 4 buttons and a scrollwheel. The extra buttons work for back and forwards.

My xorg.conf mouse section:
```
Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"mouse"
	Option 		"CorePointer"
	Option 		"Protocol" "ExplorerPS/2"
	Option 		"Device" "/dev/input/mice"
	Option 		"Buttons" "7"
	Option 		"ZAxisMapping" "4 5"
	Option 		"ButtonMapping" "1 2 6 3 7 10 11"
	Option 		"Emulate3Buttons" "false"
EndSection
```

You'll notice in the button mapping line, 6 and 3 are switched. You probably don't want yours like that. I have what is meant to be the right click button doing back and one of the extra buttons doing right click which is why those numbers are the wrong way round.

For further info on configuring mice, try here:

[http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons](http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons)

Also the utility xev (just type it in the terminal) is useful for working out which button on your mouse is which number. Just put your mouse pointer in the window that pops up when you start xev and press buttons. You'll see the button numbers reported in the terminal.

---

### Post by PiggiePaul on 2008-02-16
Thanks.

Well I modified mine to read:


Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
[COLOR="Blue"]Option 		"Buttons" "7"[/COLOR]
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

And it made no difference.


I just ran that terminal program and got the following answers.

Left "normal" button = 1
Middle "scrollwheel" button = 2
Right "normal" button = 3
My scroll wheel up/down = 4 and 5


Extra "left hand" button (which I'd like to do the BACK command in Firefox) = 2 also.
Extra "right hand" button (which I'd like to do the FORWARD command in Firefox) = 3 also

Two things I'm puzzled about (apart from it not working yet!)

why does my config say: [COLOR="Blue"]Option "Emulate3Buttons" "true"[/COLOR] when most of the example have this as [COLOR="Blue"]false[/COLOR]

and why do I have the line that reads: [COLOR="Blue"]Option "Protocol" "ImPS/2"[/COLOR] when all other examples I've seen say [COLOR="Blue"]"Protocol" "ExplorerPS/2"[/COLOR]

---

### Post by Krydahl on 2008-02-16
Because you haven't changed the file yet?

I'm guessing that if 'buntu doesn't recognise the mouse it will set things up for a basic config that will get left and right buttons working ok but not much else.

Take a back up and try changing some of the settings that look different in the examples you've seen.

---

### Post by oldsoundguy on 2008-02-16
because you INSTALLED that mouse configuration when you installed the system.  There are options for the MOUSE when you install Ubuntu or any of it variants initially.  You just clicked YES to the defalt mouse options when you loaded it.  Now you have to make the modifications because of that.

---

### Post by PiggiePaul on 2008-02-16
Ok, time for an update:

It's now All Sorted :)

First, I made a Boo Boo (after reading on Wikipedia about using the newer [COLOR="Blue"]ExplorerPS/2[/COLOR] Protocol.

As (would you believe) if I change my:

[COLOR="Blue"]Option "Protocol" "ImPS/2"[/COLOR]

to:

[COLOR="Blue"]Option  "Protocol" "ExplorerPS/2"[/COLOR]

Then Bizarrely enough Ubuntu boots up with a warning about only being able to run in low-res graphics mode. (no I don't understand it either !!!)
But that happened the other day, when I made the same change, so changing that definatly has that effect.

Anyhow, I changed it to "[COLOR="Blue"]Auto[/COLOR]" as I saw from some others Wikipedia examples and it's happy with that.

So, (with some stab in the dark luck) Here is my 100% fully working version for my "Microsoft Trackball Optical"

```


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto"
	Option		"Buttons"		"7"	
	Option		"ZAxisMapping"		"4 5"
	Option		"ButtonMapping"		"1 2 3 6 7"
	Option		"Emulate3Buttons"	"false"
EndSection
```

I hope this also may help someone else with the same device.

---

### Post by Krydahl on 2008-02-16
Well mine's set to ExplorerPS/2 and it gives me no such warning - it also isn't running in low res.

Are you sure you changed it in the mouse section of your xconf file?

---

### Post by PiggiePaul on 2008-02-16
> **Krydahl said:**
> Well mine's set to ExplorerPS/2 and it gives me no such warning - it also isn't running in low res.

Are you sure you changed it in the mouse section of your xconf file?

Yes, 100% without question.

I just edited out the word and changed them to the other version.

As I said, I did the same mod (to this 1 line) the other night and the same (can only run in low res graphics) message appeared on bootup.

what on earth the two have related to each other I've no idea.
But that's what it does 100% definate.

But, hey, Auto works fine, so I'm not complaining.

On this same subject:

(question to anyone)

If there a way I can get the scroll wheel to move the screen up and down a bit faster?

I have to scroll quite a lot to move up and down a web page.

---

### Post by Krydahl on 2008-02-16
Weird. Oh well, as long as it works. :)

On the scroll speed, I've no idea. This looks like it may give you some pointers:

[https://answers.launchpad.net/ubuntu/+question/9200](https://answers.launchpad.net/ubuntu/+question/9200)

Though they're talking about too fast rather than too slow. Looks like there's some stuff you can configure easily in Firefox if you're only having this problem in the browser. The other stuff was getting into kernel modules. Can't offer any help there, sorry.

---

### Post by PiggiePaul on 2008-02-16
> **Krydahl said:**
> Weird. Oh well, as long as it works. :)

On the scroll speed, I've no idea. This looks like it may give you some pointers:

[https://answers.launchpad.net/ubuntu/+question/9200](https://answers.launchpad.net/ubuntu/+question/9200)

Though they're talking about too fast rather than too slow. Looks like there's some stuff you can configure easily in Firefox if you're only having this problem in the browser. 



Thanks.
did this in Firefox:

[COLOR="Blue"]about:config[/COLOR]

Then alter these two lines:

[COLOR="Blue"]mousewheel.withnokey.numlines
mousewheel.withnokey.sysnumlines[/COLOR]

Edit the 1st one to the amount [COLOR="Blue"]6[/COLOR]
Edit the 2nd one to say [COLOR="Blue"]FALSE[/COLOR]

---

### Post by whsutton on 2008-04-10
I have the the same mouse :guitar: And after looking through the mounds of "do this & -do that" Your solution worked!! 

Thank you so very much!!:):):)
Now I can relax my thumb now:lolflag:

Thanx again:)

---

