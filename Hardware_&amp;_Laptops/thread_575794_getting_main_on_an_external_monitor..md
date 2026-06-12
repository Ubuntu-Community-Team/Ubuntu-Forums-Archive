---
title: "getting main on an external monitor."
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by Koziasty on 2007-10-14
Honestly,  I know this topics similar, but i actually cant get anything to work ;(

My problem is: I hardly ever work on multiple monitors, but from time to time I like to watch a film or a series on my TV. My TV being a 1380x768 lcd, connecting to the laptop via monitor connection.  

So what I really want to do: without turning off my laptop, attach a cable to the monitor and the laptop, press a button and voila, here I go. I dont really care, if there is a display on my laptops LCD. (i.e. i think, swapping my main display onto the TV)

Possible? 

I run an ATI card on 'ati' driver. My native resolution is 1280x800. I run gutsy. 

Thanks

---

### Post by danpre on 2007-10-14
> **Koziasty said:**
> Honestly,  I know this topics similar, but i actually cant get anything to work ;(

My problem is: I hardly ever work on multiple monitors, but from time to time I like to watch a film or a series on my TV. My TV being a 1380x768 lcd, connecting to the laptop via monitor connection.  

So what I really want to do: without turning off my laptop, attach a cable to the monitor and the laptop, press a button and voila, here I go. I dont really care, if there is a display on my laptops LCD. (i.e. i think, swapping my main display onto the TV)

Possible? 

I run an ATI card on 'ati' driver. My native resolution is 1280x800. I run gutsy. 

Thanks

Don't you have a switch on your laptop to send a signal to external monitor?
Blue signs on keybord?
Combination like FN + F4?

or if you want to use dual monitor try this [howto]("http://ubuntuforums.org/showthread.php?t=361124&highlight=gutsy+second+monitor+intel")

---

### Post by MaximusTG on 2007-10-15
[http://ubuntuforums.org/showthread.php?t=561865](http://ubuntuforums.org/showthread.php?t=561865)

Check out my thread above.
I faced a similar problem, where I wanted to dynamically switch between monitors. The same problem applies to you. You will need to install Gutsy for this however.. (or update the needed packages in Feisty but that's tricky) 
Then you can simply use the xrandr commandline tool like this:

xrandr --output VGA --auto --output LVDS --off

to turn on the VGA display

and

xrandr --output LVDS --auto --output VGA --off

---

### Post by Koziasty on 2007-10-27
It did take me a while to answer, sorry about that.

So, the suggestion about using Fn keys, unfortunatelly, didnt work.

Using the xrandr solution helped me to make a step in the right direction - now I can get screen on the TV, but the TV is not using its 'native' resolution (it works @ 1280x768, 60Hz, it should work @ 1360x786, 60Hz). The problem is, I can't get the TV to display anything more than 1280x768 - an error comes out. I did an additional line, with the proper resolution, but it won't work, saying that the furthest it can go, is 1280x1024. Which is not helpful, believe you me :]

Any help would, of course, be appreciated. 

Koziasty

---

