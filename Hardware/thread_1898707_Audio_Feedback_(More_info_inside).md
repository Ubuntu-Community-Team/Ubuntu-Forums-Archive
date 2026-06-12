---
title: "Audio Feedback (More info inside)"
date: 2011-12-22
forum: Hardware
---

### Post by Pyro.699 on 2011-12-22
Alright, so as it stands right now im getting a bit of feedback from a  particular setup. I have done quite a bit to try and figure out exactly  what is causing it and have come up empty.
The end goal is for me  to have my two computer systems (One running windows 7 and the other  using ubuntu) share a common audio system. I connect the line-out (on  the linux machine) to the line-in (on the windows machine) and then  connect the line-out (on the windows machine) to the audio system. When  it is setup like this i get a lot of feedback (high pitched squealing).
Here is what i have done to try and figure out / fix the problem.

[LIST]
[*] Unplugged the line-in (on the windows machine) to make sure that the feedback was not originating on the windows machine.
[LIST]
[*]The feedback went away.
[/LIST]
[*]I then plugged the audio system directly into the linux machine through its line-out.
[LIST]
[*]The feedback went away.
[/LIST]
[*]I  then removed the case of the linux machine; took the motherboard out  and placed it on a piece of cardboard with nothing plugged in but the  psu. Plugged the line-out (on the linux motherboard) into the line-in  (on the windows machine).
[LIST]
[*]Having the PSU connected and the machine turned off, the feedback was still present.
[/LIST]
[*]I tried a different source going into the line-in (on the windows machine), it was my phone.
[LIST]
[*]There was no feedback.
[/LIST]
[*]The  cable i was planning on using to connect the wires was long and ended  up being colied. I thought that maybe the cable could be causing the  feeback so i replaced it with a high quality shorter wire.
[LIST]
[*]There was still feedback.
[/LIST]
[*]I tried plugging in a [USB Sound Board]("http://www.phidgets.com/products.php?product_id=3401") and used that as my line-out (on the linux machine) rather than the one located on the motherboard.
[LIST]
[*]There was still feedback.
[/LIST]
[*]I tried plugging in a [USB Sound Board]("http://www.phidgets.com/products.php?product_id=3401") and used that as my line-out AND my line-in (on the windows machine).
[LIST]
[*]There was still feedback.
[/LIST]
[/LIST]
 
The motherboard for the windows computer is: **ASUS P5N-D**
The motherboard for the linux computer is: **EVGA nForce 780i SLI**
 
Is  there any advice that anyone could give me that could help fix this problem?
 
Thanks
~Cody Woolaver

---

### Post by pommie on 2011-12-22
Going back to when stereo's were separate components, you could not connect one amplifier to another unless the one doing the output had a pre-amp line out or the one receiving was a linear amplifier, designed to take a amplified input, and amplify it even more.

You are putting an amplified signal into an input designed for microphones, not amplified, I would guess that the squeal you are hearing is not feedback but the overload protection working its little heart out.  

While I am frequently wrong, the only sound cards I have seen with pre-amp output are the 'pro' type, and they cost a lot.

 Cheers David

---

### Post by coldraven on 2011-12-22
With four resistors you could balance the connection. 

OUTPUT --------------------10K resistor------------INPUT
                               |
                          10 Ohm resistor
                               |
GROUND---------------------------------------------GROUND

The output sees a low resistance as if there were headphones plugged in.
You can try a slightly higher resistor, maybe up to 100 Ohms
The input sees a high resistance as if a microphone was the source.
You need to do this for each of the stereo channels.
Edit:the forum has removed the whitespace that I used. Just imagine that the 10 Ohm resistor is ten characters to the right :)

---

### Post by Pyro.699 on 2011-12-22
> **pommie said:**
> Going back to when stereo's were separate components, you could not connect one amplifier to another unless the one doing the output had a pre-amp line out or the one receiving was a linear amplifier, designed to take a amplified input, and amplify it even more.

You are putting an amplified signal into an input designed for microphones, not amplified, I would guess that the squeal you are hearing is not feedback but the overload protection working its little heart out.  

While I am frequently wrong, the only sound cards I have seen with pre-amp output are the 'pro' type, and they cost a lot.

 Cheers David
Could you link me to one that might solve my problem xD Im prety open to any solution; i might be able to find a second hand card somewhere...

> **coldraven said:**
> With four resistors you could balance the connection. 

OUTPUT --------------------10K resistor------------INPUT
                               |
                          10 Ohm resistor
                               |
GROUND---------------------------------------------GROUND

The output sees a low resistance as if there were headphones plugged in.
You can try a slightly higher resistor, maybe up to 100 Ohms
The input sees a high resistance as if a microphone was the source.
You need to do this for each of the stereo channels.
Edit:the forum has removed the whitespace that I used. Just imagine that the 10 Ohm resistor is ten characters to the right :)
Think you could explain this a bit more xD I failed my electrical engineering course and suck with that kinda crap. I know i could get the resistors[]("http://here") [here](http://www.alliedelec.com/) but after i got them id have no idea what to do with them and how to modify the wire. Also which cable would this be going on? The one that is linking the two towers (line-out from the linux and line-in on the windows). It is a stereo wire, so i assume that i need to do this to both the right and left channel?

Thanks guys
~Cody

---

### Post by coldraven on 2011-12-28
Pyro, does this help?

Hi, you need to cut the cable that you use to link the PCs and add what  I've shown. I changed the 10 Ohm resistors to 30 Ohm after I measured  the resistance of my headphones.
If you bend the resistor wire over on itself at the ends it could help  to grip the wire as you solder it Or use a strip board.
[http://en.wikipedia.org/wiki/Strip_board](http://en.wikipedia.org/wiki/Strip_board)
To make a neat job try and find a small plastic box.Drill a hole in each  end for the Jack cable to pass through. Then either put a knot in the  cable or use a cable tie to stop the cable pulling out and damaging your  circuit.
Good luck :)

---

### Post by coldraven on 2012-01-03
Hi, Try this, I didn't know what size your board is but you can cut it down if you want.
You don't have to follow my plan hole for hole as long as you don't mix up the strips.
Don't burn your fingers :)

Big thanks to Martin Oldfield for the stripboard template.
[http://mjo.tc/atelier/2009/02/draw-sboard.html](http://mjo.tc/atelier/2009/02/draw-sboard.html)

---

