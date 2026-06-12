---
title: "Switch KeyboardLayout"
date: 2005-12-04
forum: General Help
---

### Post by JimS on 2005-12-04
Objective:  Be able to switch between English and Danish keyboards.

I went to Keyboard Preferences - Layout tab and added Danish.  But there are no
directions on how to switch layouts.  :( 
So I clicked on HELP and it says to "see the “Keyboard Layout Switcher” manual."
Where is this manual?  :???: 
How do I switch back and forth between Danish and English?  :???: 
This is very easy in Susa Linux and MS Windows using the setup windows.  :) 
But Ubuntu seems to come to a dead end before finishing the setup.  :confused: 

JimS

---

### Post by sethmahoney on 2005-12-06
Assuming you're using Ubuntu and not Kubuntu, here's what you need to do:
Right-click on an empty spot on your panel and click "add applet" or whatever it is.  A window will pop up with a bunch of applets you can add - the one you want is called "language selector" or something like that.  Once you get that on your panel, just click on it to change your keyboard layout.  You can also set up a hotkey to switch somewhere in the language settings (in the System->Preferences menu).  Hope this helps!

---

### Post by spier on 2005-12-06
[QUOTE=sethmahoney]Assuming you're using Ubuntu and not Kubuntu, here's what you need to do:
Right-click on an empty spot on your panel and click "add applet" or**whatever it is** 
...
the one you want is called "language selector" **or something like that**.  
...
Hope this helps![/QUOTE]

as I was a bit nervous with my beginner's frustration,  I suposed you was  kidding with those vague hints, but then I tried to accomplish the OP intend, and, believe it, I just resolved my major problem that was the challenge to set my English keyboard to write in Brazilian speech, with those &#231;, &#227;, &#244;, &#252; nice characters ;) 

Well, this or just my 11th try :???: 

But now I have a switcher in my panel where I can choose between "USA" or "USA*", and it works even better than I was expecting!
 
BTW, in my Ubuntu 5.10 it reads as 

Right-click on an empty spot on your panel and click "**Add to panel**
...
the one you want is called **Keyboard Indicator**.  
...

Thank you very much!!!

---

### Post by sethmahoney on 2005-12-07
[QUOTE=spier]as I was a bit nervous with my beginner's frustration,  I suposed you was  kidding with those vague hints, but then I tried to accomplish the OP intend, and, believe it, I just resolved my major problem that was the challenge to set my English keyboard to write in Brazilian speech, with those ç, ã, ô, ü nice characters ;) [/QUOTE]

Yeah, sorry about the vagueness - I wasn't on my Ubuntu machine when I wrote that.  But I'm glad it worked for you!

If you want to set up a keyboard shortcut, this should get you going:
Click System, then Preferences, then Keyboard Preferences.
Go to the third tab: Layout options
Click on "Group Shift/Lock Behavior"
A bunch of check boxes will show up.  Select one, and it will set whatever option is next to it to toggle your keyboard layout.
For example, I checked "Both Alt keys together change group", and now whenever I hold down both Alt keys together, my keyboard layout changes from English to Russian or from Russian to English.
This is REALLY handy when your screensaver has come up and you seem to be stuck in the wrong keyboard layout.

---

### Post by JimS on 2005-12-08
Many thanks.   :D  :D  :D 

I now have my Danish Æ Ø Å æ ø å letters working
using the mouse to switch between Danish and English.

Now for a second question.  
How may I switch using the keyboard?  :confused: 
I hate switching between mouse and keyboard.  :( 

JimS
formerly from Vancouver (not BC) Washington (not DC)

---

### Post by sethmahoney on 2005-12-12
(Sorry about the delay in getting a response to you):
Go to System->Preferences->Keyboard
Click the "Layout Options" tab.
Click "Group Shift/Lock Behavior".
Check one of the boxes that comes up.  I use "Both Alt keys together change group".
Now, whenever you hit the key combination you chose, it will toggle the keyboard layout.

---

### Post by JimS on 2005-12-13
You 
  are 
    the
       MAN.
:) :) :) :) 
Works great.  I had tried this before,
but probably did something wrong
as it would toggle once, but not back.  
Now it toggles quiickly back and forth,
Just like I want.

1000 thanks
tusan tak

JimS

---

### Post by ashrack on 2005-12-13
Added the Keyboard Indicator to the panel. Is there a way that insted of showing "letters" it would just show the flag of the country?

---

### Post by ashrack on 2005-12-13
Added the Keyboard Indicator to the panel. Is there a way that insted of showing "letters" it would just show the flag of the country?

---

### Post by spier on 2005-12-13
Ok, now I also have a keyboard shortcut,  always better than a search on the mouse pointer, thanks for the tip!

Both Alt keys also seemed a good choice, but i had to leave it since, after toogling to my "native" keyboard, trying Alt+Alt again didn't work, maybe something with "composed keys" that depend on the Alt key.  Now I'm using Ctrl+Ctrl, and I can live with it! ;-)

---

### Post by JimS on 2005-12-15
Spier,

Glad to see you got it working also. \\:D/ 

The toggle I use is Contol Shift.
I touch type, so my left little finger
has learned to lay on both keys together
for toggling.

Alt Alt looked a good choice.
But It didn't work for me.
Toggled once and died,
leaving me stranded.  :mad: 

JimS
Prostate Cancer Aware

---

### Post by ashrack on 2005-12-15
[QUOTE=ashrack]Added the Keyboard Indicator to the panel. Is there a way that insted of showing letters it would just show the flag of the country that is currently selected for keyboard layout?[/QUOTE]
:confused:

---

### Post by sethmahoney on 2005-12-16
[QUOTE=ashrack]Added the Keyboard Indicator to the panel. Is there a way that insted of showing "letters" it would just show the flag of the country?[/QUOTE]

As far as I know, the answer is no, and I think I remember reading somewhere that this will never be added to Gnome, for social, political, and practical reasons.

---

### Post by ashrack on 2005-12-16
[QUOTE=sethmahoney]As far as I know, the answer is no, and I think I remember reading somewhere that this will never be added to Gnome, for social, political, and practical reasons.[/QUOTE]

anyway to manually add it?

---

### Post by spier on 2005-12-16
[QUOTE=sethmahoney]As far as I know, the answer is no, and I think I remember reading somewhere that this will never be added to Gnome, for social, political, and practical reasons.[/QUOTE]

Ok, but allowing some translaction would be good social and political features, maybe just not practical  :p 

I.e., actually I'm using  US keys for programming - shows as "USA" in panel, that is fine -  and Portuguese for writting, that shows as "USA*", not exactly what its supposed to be.  Note that I'm using a laptop with a generic keyboard, where the Brazilian layout do not apply.  

But the expected functionallity works great!

---

### Post by sethmahoney on 2005-12-17
[QUOTE=spier]Ok, but allowing some translaction would be good social and political features, maybe just not practical  :p 

I.e., actually I'm using  US keys for programming - shows as "USA" in panel, that is fine -  and Portuguese for writting, that shows as "USA*", not exactly what its supposed to be.  Note that I'm using a laptop with a generic keyboard, where the Brazilian layout do not apply.  

But the expected functionallity works great![/QUOTE]

No doubt they could do a lot better with what the keyboard indicator applet shows.  Another example: It shows "RUS" for Russian, not "&#1056;&#1059;&#1057;".

---

### Post by simosx on 2006-01-28
[QUOTE=ashrack]Added the Keyboard Indicator to the panel. Is there a way that insted of showing "letters" it would just show the flag of the country?[/QUOTE]

There is a policy not to use flags as it is contentious for some countries and regions; China and Taiwan, Greece and Skopje, and so on...

---

### Post by ashrack on 2006-01-28
But still, is there a way I could have it on my own computer?

---

### Post by simosx on 2006-01-28
[QUOTE=sethmahoney]No doubt they could do a lot better with what the keyboard indicator applet shows.  Another example: It shows "RUS" for Russian, not "&#1056;&#1059;&#1057;".[/QUOTE]

Apparently there is no translation yet for these words in Russian.:-k 

If you can spare the 60 minutes, the file to update is found
[http://translation.sourceforge.net//HTML/domain-xkeyboard-config.html](http://translation.sourceforge.net//HTML/domain-xkeyboard-config.html)

---

### Post by simosx on 2006-01-28
[QUOTE=ashrack]But still, is there a way I could have it on my own computer?[/QUOTE]

Of course there is, as all the software is open-source.\\:D/  However, it may require some programming effort.

The applet for the Keyboard Indicator is called internatlly gswitchit, available from
[http://cvs.gnome.org/viewcvs/gnome-applets/gswitchit/](http://cvs.gnome.org/viewcvs/gnome-applets/gswitchit/)

---

### Post by simosx on 2006-01-28
[QUOTE=spier]Ok, but allowing some translaction would be good social and political features, maybe just not practical  :p 

I.e., actually I'm using  US keys for programming - shows as "USA" in panel, that is fine -  and Portuguese for writting, that shows as "USA*", not exactly what its supposed to be.  Note that I'm using a laptop with a generic keyboard, where the Brazilian layout do not apply.  

But the expected functionallity works great![/QUOTE]

The "USA*" you have is most probably the US International keyboard, which indeed allows to write accented characters. It shows the * because there is already a layout with the same name.

What I would recommend you is to add the Brazilian layout instead. The Brazilian keyboard layout supports all characters you require in Brazilian Portuguese.

I have prepared a Flash animation that demonstrates how to enable Brazilian Portuguese, at
[http://planet.hellug.gr/misc/bra/](http://planet.hellug.gr/misc/bra/)

---

### Post by jazzgossen on 2006-02-02
Speaking of different keyboard layouts - is there a way to specify a default layout for a certain program? For example, I'd like my emacs sessions to default to a US keyboard layout, and my mail program to default to Swedish.

---

### Post by dcstar on 2006-02-02
[QUOTE=jazzgossen]Speaking of different keyboard layouts - is there a way to specify a default layout for a certain program? For example, I'd like my emacs sessions to default to a US keyboard layout, and my mail program to default to Swedish.[/QUOTE]
Possibly you could modify the launcher for each program to somehow specify the keyboard, but you'd have to dig deep in the Gnome (or application) man pages to see if such a thing is possible.

It could be worth the effort......

---

### Post by spier on 2006-02-16
[QUOTE=simosx]The "USA*" you have is most probably the US International keyboard, which indeed allows to write accented characters. It shows the * because there is already a layout with the same name.

What I would recommend you is to add the Brazilian layout instead. The Brazilian keyboard layout supports all characters you require in Brazilian Portuguese.

I have prepared a Flash animation that demonstrates how to enable Brazilian Portuguese, at
[http://planet.hellug.gr/misc/bra/](http://planet.hellug.gr/misc/bra/)[/QUOTE]


Hi, sorry for the delay, and thanks for the tutorial! I'll be forwarding the link to some guys!

This works for keyboards with brazilian layout (there are two main layouts, both showed under Brazil's avaliable layouts), usually what we got for desktop. 
But laptops have usually US keyboards, thus a US international solution.  

I'll give it another try soon - my laptop is at home, and will let you know!

---

### Post by JimS on 2007-07-22
...
Upped to Ubuntu Edgy and lost my USA/Denmark keyboard switching ability.
Got it back, except no USA or DK on panel.
How do I get USA or DK to show on panel?

Also have a notebook with Xubuntu Feisty and haven't tried getting
USA/Denmark keyboard installed.  Will I have the same issues?

JimS
kaj.advancingwithus.com
...

---

