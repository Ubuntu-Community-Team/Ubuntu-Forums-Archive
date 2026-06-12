---
title: "Laptop Speakers / Headphone jack Inseperable"
date: 2008-07-22
forum: Hardware
---

### Post by sixblades on 2008-07-22
So here's the deal:

I can get sound out of my laptop speakers, and when I plug my headphones into the headphone jack I get sound out my headphones, which is all nice and shiny. The problem is that when I plug in my headphones, the laptop speakers keep playing, which is a bit of a conundrum because I'm using headphones to avoid disturbing other people around me.

I downloaded an ALSA GUI mixer and played with all the different levels while my headphones were plugged in and the speaker and headphone volume were "linked" in all cases (both volumes would be equally adjusted by a single control).

So I'm wondering if there are any hidden or sneaky fixes that I should know about. It seems like a fairly simple issue, so I'm hoping that the solution isn't too complicated (although I'm willing to try a complication resolution ;)).

Note:
I think that my sound card is one of those ones that has "universal jacks" because I can plug my headphones into any port (when in Windows XP) and it will ask me which device I just plugged in and use software to handle it accordingly. This means that I can plug my headphones into the microphone jack and my computer will be just fine with that. In Windows.

---

### Post by phidia on 2008-07-23
You need jack sense but getting that working in ubuntu can be troublesome.
What sound card do you have? Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=500894&page=3") and the links provided there.

---

### Post by aeriiz on 2008-07-23
You can manually mute "Front" in volume control if you use Alsa mixer.

---

### Post by sixblades on 2008-07-25
**@phidia:**
     Thanks for the link. I followed it and a few others inside it, but I still can't seem to get the problem fixed. I tried to get jack sense to work but couldn't seem to get any solid leads on that. I'm not sure what sound card I have. How can I find out?

**@aeriiz:**
     To quote myself:
> I downloaded an ALSA GUI mixer and played with all the different levels while my headphones were plugged in and the speaker and headphone volume were "linked" in all cases (both volumes would be equally adjusted by a single control).
     Notice the "**all**". I've tried adjusting every single level. I appreciate the response, but please read posts a bit more carefully before responding.

---

### Post by ARhere on 2008-07-25
> **sixblades said:**
> 
Note:
I think that my sound card is one of those ones that has "universal jacks" because I can plug my headphones into any port (when in Windows XP) and it will ask me which device I just plugged in and use software to handle it accordingly. This means that I can plug my headphones into the microphone jack and my computer will be just fine with that. In Windows.

Uhhh.... you already know then that your sound card outputs are firmware controlled and not hardwired audio output/inputs.  I have designed with these units before and while they are "neat", they become unusable without the original controlling software.  If the vendor of the sound card does not offer a Linux driver, then you might be SOL.

What is your soundcard maker/chipset and I will help you look.

-AR

---

### Post by sixblades on 2008-07-25
**@ARhere:**
Yeah, I was thinking it was going to be something along those lines.
Info:
Soundcard = Realtek ALC 888
Chipset = Intel® PM965 + ICH8-M

[Here]("http://www.msicomputer.com/NB/product_spec.asp?model=MS-163A")'s a link to the notebook manufacturer's page for my model:

---

### Post by ARhere on 2008-07-25
Nothing yet, but I have ran across a large number of posts in other forums talking about the same problem.  The only promising thing is this chipset is used by Dell, who is (*some what*) Linux friendly.  You might get somewhere with Dell support, either online or phone.

-AR

---

### Post by Slug71 on 2008-07-26
Hey man, the same thing happened to me till yesterday but but then i just unplugged the external speakers from the earphone jack and plugged it right back in and it worked fine. Weird i know. But i have to do it every time i log in to Ubuntu. And today its decided to give a staticy noise through either speakers?! Frustrating!!

---

### Post by sixblades on 2008-07-26
**@ARhere:**
Thanks. I'll give that a try and see if I can get anywhere. I've been crawling the forums and have tried everything that's been suggested, but to no avail. I've discovered that by ALMOST muting the front channel the speakers become inaudible and I can just use an external amp, but this doesn't really cut it when I have just my headphones (and it's really just a cheap workaround anyway).

---

### Post by Slug71 on 2008-07-26
Yeah this whole sound thing is really p...... me off! Specially that my internal mic wont work. I really hope all this is gonna be fixed in 8.10 Intrepid. Else its back to Windows for me.Noooooooooooooooooooooooo!!

---

### Post by ARhere on 2008-07-27
I hate to say it, but I am running out of ideas as well.

Keep in mind that this is not an Ubuntu issue, but a laptop/hardware vendor issue.  Laptops are a lot "less standard" (*if that even makes sense*) then a typical desktop.  It is not too uncommon for pieces of a laptop not to work when used with a different OS then what it was preloaded with.

I think this is why most forum Administrators want to see Ubuntu pre-installed and not just passed out on street corners.

Sorry  -AR

---

### Post by Slug71 on 2008-07-27
Yeh thats what i was starting to think. Which is one of the reasons i dont really like laptops much. Managed to get rid of the static but my sound doesnt seem to be as loud as with windows. I could be wrong though. I think my alsa isnt configured correctly either. 
Its weird that my integrated webcam works though but not my mic. My printer wasnt detected either.

---

### Post by sixblades on 2008-07-27
**@ARhere:**
Yeah, I know. I gathered enough at the beginning that the sound card's firmware/hardware setup would cause some significant problems if the correct drivers weren't provided, which they obviously aren't (for linux). This is a real shame, because I use linux to surf the web, program, and listen to music (all things that it does fantastically, by the way). Unfortunately, this means that I will likely be spending more time in XP if I can't get this audio issue resolved. Still, thanks for the effort, AR. I'll post an update if I manage to make any progress.

On a somewhat related note, what exactly is pulseaudio, and how does it differ/compare to ALSA?

---

### Post by Slug71 on 2008-07-27
From what i understand but could be totally wrong is that PulseAudio is a sound server. It works alongside Alsa into making it think that you have a soundcard present when all you have is a sound chip/procesesor, if that makes sense. But i could be wrong.

I really hope that 8.10 Intrepid is gonna have the latest kernel if it doesnt already and the latest alsa installed. Hopefully that will solve these these issues. Untill then ill probably install and dual boot with Vista.

---

### Post by Ramaddan on 2008-07-27
Did you take a look at this?

I had a similar problem and solved it. Hope it helps.

[http://ubuntuforums.org/showthread.php?t=871370]("http://ubuntuforums.org/showthread.php?t=871370")

---

### Post by sixblades on 2008-08-05
Fantastic Ramaddan! That worked flawlessly. I can't express how grateful I am for your solution. Now I can program in Ubuntu AND listen to music!

To anyone else that is having this problem, try clicking on the above link if you have a similar chipset.

Once again, thanks. :)

---

