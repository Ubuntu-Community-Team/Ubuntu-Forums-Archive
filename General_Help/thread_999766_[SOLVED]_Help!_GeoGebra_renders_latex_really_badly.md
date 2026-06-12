---
title: "[SOLVED] Help! GeoGebra renders latex really badly!"
date: 2008-12-02
forum: General Help
---

### Post by smain on 2008-12-02
Hi all

I really need help on this one, because I'm going to do a report in physics very soon. I use GeoGebra to create different kinds of graphs and drawings (like triangles, angles, vector that kind of stuff ^-^)

However when i insert some text and choose it to be latex, so that i can have equations on the drawing, they render really badly. Any kind of text that is not latex is as sharp as ever, but the latex is very blurry.

I export the pictures as .png since thats what I need. I have uploaded a picture with this to show what i mean. Please someone help me! :S

Smain

---

### Post by TeXtonyx on 2008-12-02
> **smain said:**
> Hi all


I export the pictures as .png since thats what I need. I have uploaded a picture with this to show what i mean. Please someone help me! :S

Smain

math247.pbwiki.com/f/lesson6.pdf
This may be helpful in general.

Did you know there is a geogebra forum where the response
may be more experienced and quicker than this venue. 

[http://www.geogebra.org/forum/viewtopic.php?f=2&t=3036](http://www.geogebra.org/forum/viewtopic.php?f=2&t=3036)
[http://www.batmath.it/interattive/ggb_tutorials/texts/texts.htm](http://www.batmath.it/interattive/ggb_tutorials/texts/texts.htm)

I thought I would pass along what I found to be the best of the
latex to html converters, TeX4ht, by Eitan Gurari. Good Luck!

---

### Post by smain on 2008-12-02
> **TeXtonyx said:**
> math247.pbwiki.com/f/lesson6.pdf
This may be helpful in general.

Did you know there is a geogebra forum where the response
may be more experienced and quicker than this venue. 

[http://www.geogebra.org/forum/viewtopic.php?f=2&t=3036](http://www.geogebra.org/forum/viewtopic.php?f=2&t=3036)
[http://www.batmath.it/interattive/ggb_tutorials/texts/texts.htm](http://www.batmath.it/interattive/ggb_tutorials/texts/texts.htm)

I thought I would pass along what I found to be the best of the
latex to html converters, TeX4ht, by Eitan Gurari. Good Luck!

I think you are getting me wrong. These files and places that you refer to merely tell me how to use the latex in GeoGebra. I already know that. My problem is as said that the latex I create in GeoGebra seems very blurry when exported (I need to export my drawings as .png so I can put them in a OO.o document).

Therefore what I need to do is to find out how to remove the blur from the latex when exported.

Also I don't see what a latex to html converter has to do with my problem in anyway o.O, I don't need my files as html and also they are not in the .tex format but as .ggb files which is what GeoGebra saves in.

Anyway. I still need help to solve my problem, so more suggestions are welcomed :p

Smain

---

### Post by TeXtonyx on 2008-12-02
Edited

---

### Post by TeXtonyx on 2008-12-02
> **smain said:**
> I think you are getting me wrong. These files and places that you refer to merely tell me how to use the latex in GeoGebra. I already know that. My problem is as said that the latex I create in GeoGebra seems very blurry when exported (I need to export my drawings as .png so I can put them in a OO.o document).

Therefore what I need to do is to find out how to remove the blur from the latex when exported.

Also I don't see what a latex to html converter has to do with my problem in anyway o.O, I don't need my files as html and also they are not in the .tex format but as .ggb files which is what GeoGebra saves in.

Anyway. I still need help to solve my problem, so more suggestions are welcomed :p

Smain

Well, it's quite common to have to build a webpage in college,
especially if you continue and present webpages for students.
So the TeX4ht was an aside, intended for future reference, and 
the analogy connection is faithful conversion of equations from 
one format to another. It's not like I suggested a better tool
than Beamer for making slide show presentations. 

I politely suggested that you use the geogebra forum (or a latex)
because of all the thousands of posts on this forum, there were
only 14 on the topic of geogebra, most of them simple, and no
solutions or questions asked about actual equation problems.
Since you seemed to indicate a time constraint, isn't it better
to move to a spot where the fish are biting? I'm not saying that
it is anyway improper or off-topic, but that it is inefficient
to expect any timely (topical) helpful response on this forum. 

Now on the geogebra forum it took me about 30 seconds to find the
following thread, which though it may not be the answer to your
question, is at least an answer to an exporting question in the
same ballpark as yours, rather than waiting to strike out at
the plate on this forum which is nearly certain (in time).


---------------------------------------------------
Question: "Is there a way to export the picture that I draw in 
GeoGebra to Latex? Would you show me how?" 

Answer:

"Export -> Drawing pad as PSTricks.

This creates a self contained LaTeX document. If you read this, 
it should be obvious where the picture begins and ends. I've 
made extensive use of PSTricks, before I found GeoGebra. It's a 
very useful set of LaTeX macros. Note that these macros create 
postscript, so you can't use pdfLaTeX directly, you must create 
a .ps file and then distill this. ...

------------

Next create your GeoGebra worksheet.

Using the menus follow, File -> Export -> Drawing pad as PSTricks.

This opens a new window with a couple of options.

"Generate PSTricks code".

Copy and paste the code. Note this is an entire LaTeX document. 
You may only need part of this if your figure is part of a larger
document. But, if you are used to LaTeX itself, then it should 
be clear which parts to extract."

--------------------------------------------- 

There isn't a response nearly as relevant on all the Ubuntu forums.

"Anyway. I still need help to solve my problem, so more 
suggestions are welcomed :p " 

Cultivate the virtue of persistence and quell the waste of arrogance.

The two most useful skills to succeed with computer endeavors are 
develop excellent search tactics and read/*follow* the directions. 
That hard-earned wisdom is for everybody, and isn't specific to you.

Now if you followed my advice and posted your question on a forum
where you stood a good chance to get a timely answer, *besides*
asking on this forum, you have executed a good search strategy.
And you heeded my advice that it was wishful thinking to expect
a timely answer on this forum so followed the direction to a 
much more suitable alternative search forum (or a latex forum).

You did an excellent thing in providing the image. But forums
related to LaTeX like to hear the steps you took and often
that means including snippets of relevant code. 

In general, the environment can be incomplete, the code can 
have an error, or incorrect steps are followed in executing 
the program. Software handles some formats better than others. 
I used to get distorted images of mathematical equations when
using latex2html conversion rather the TeX4ht conversion which 
is what reminded me of TeX4ht and .pdf versus image format.

---

### Post by smain on 2008-12-02
Sorry for the trouble :oops:... But I didn't understand that you meant I had to try there, (thought you linked to the solutions)... I tried posting on GeoGebra's forum as suggested and short after found the answer that I needed the new pre-released version...

BTW I might have gotten the sentence wrong (I'm not native english speaking) but I see no reason for you to call me arrogant because I'm asking for more suggestions

Smain

---

### Post by TeXtonyx on 2008-12-02
> **smain said:**
> Sorry for the trouble :oops:... But I didn't understand that you meant I had to try there, (thought you linked to the solutions)... I tried posting on GeoGebra's forum as suggested and short after found the answer that I needed the new pre-released version...

BTW I might have gotten the sentence wrong (I'm not native english speaking) but I see no reason for you to call me arrogant because I'm asking for more suggestions

Smain

"But I didn't understand that you meant I had to try there"
So you could figure out to post a question about GeoGebra to the
Ubuntu forum, but found the idea of posting your GeoGebra question
to a GeoGebra forum as a little too much of a challenge to think of.


I think this sentence is fairly clear and to the point.

"Did you know there is a geogebra forum where the response
may be more experienced and quicker than this venue."

[http://www.geogebra.org/forum/viewtopic.php?f=2&t=3036](http://www.geogebra.org/forum/viewtopic.php?f=2&t=3036) "

------------------------------------

"...but I see no reason for you to call me arrogant because I'm asking for more suggestions"
 
I did not call you arrogant, again this is what I wrote:

"Cultivate the virtue of persistence and quell the waste of arrogance.

The two most useful skills to succeed with computer endeavors are
develop excellent search tactics and read/*follow* the directions.
That hard-earned wisdom is for everybody, and isn't specific to you."

I separated them because the first line is really important for
everybody in all aspects of life, so that qualifies it for wisdom.
Persistence and humility are positive personality traits or virtues.
I used the phrase "quell the waste of arrogance" in place of the
word humility or gratitude because arrogance makes smart people 
stupid becausethey are inefficient. I have a good quote about the
value of Persistence, and a short one for "Ingratitude makes one 
forgetful and arrogant."

"That hard-earned wisdom is for everybody, and isn't specific to you."
For everybody who wants to use a computer quite competently the 
foremost requirements are learning how to do searches and read 
the manual. Making backups is more of a good habit than a skill. 

"Nothing in the world can take the place of Persistence. Talent 
will not; nothing is more common than unsuccessful men with 
talent. Genius will not; unrewarded genius is almost a proverb. 
Education will not; the world is full of educated derelicts. 
Persistence and determination alone are omnipotent. The slogan 
'Press On' has solved and always will solve the problems of the 
human race." quote by former President Calvin Coolidge
This ideal virtue is exemplified by President-elect Obama.

This is important to know when one  young and quite bright.
I was politely careful to avoid stating that you were arrogant. 
Now if your hunch that I implied that you were arrogant is true,
is that an untrue judgment about your character? If it is, then
I will apologize even though I didn't explicitly judge you. :-)

smain wrote: Thanks!  Exactly what I needed ^-^...
My problem is hereby solved thanks to you murkle :wink: 

So asking for a solution on the GeoGebra forum was next to do on
your todo list? I think you discounted and dismissed my suggestion,
( so I was *not* criticizing you for asking you for more suggestions)

"Did you know there is a geogebra forum where the response
may be more experienced and quicker than this venue."

because you ignored it, and I don't think it is a complex sentence or 
a hard concept to translate from one language to another. I believe
that you thought you knew enough to decide what was a good way to
pursue your question, so you ignored my advice and posted asking the
same question again which is known as beating on a dead horse. Then
you are too shallow to acknowledge the worth of my contribution, you 
would rather complain about being called arrogant. You are ignorant
about how to conduct searches. And it is arrogant to for anyone to
pretend that they know something when they don't, even if it is about
oneself. If I hadn't hammered at the solution your ignoring my advice
due to ignorance would have resulted in you not getting your problem
solved in a timely fashion. That is what I mean by arrogance making
a smart person less efficient, or affectively, a bit more stupid.

---

