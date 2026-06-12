---
title: "Using dead keys to compose unicode characters"
date: 2008-11-04
forum: General Help
---

### Post by haldrik on 2008-11-04
Hello:

I'm trying to set up my keyboard to use dead keys to input Cherokee letters (unicode 13A0-13F4) in Ubuntu Gutsy. Here is what I want to do exactly. I want to be able to switch to my custom Cherokee layout and type a consonant (assigned as one of the already existing dead keys) + a vowel key to get the corresponding Cherokee character (which represents the whole syllable). Once I get this exact method to work for ONE combination (lets say "g" plus "a" makes Cherokee "GA"), I'm sure I can get the whole keyboard customized. Here's what I've done: 

First, I've universally changed the input method to "xim".

Then, I added a new keyboard layout in /usr/share/X11/symbols/us, such that, among many other assignments, the "g" key is assigned to "dead_grave" and the "a" key (<AC01>) is assigned to the Cherokee vowel A. ( Here are the relevant lines from that file):

key <AC01> { [ 0x10013A0,  a,  	A,  A ] };
key <AC05> { [ dead_grave, g,	G,  G]  };

(When I use this keyboard layout, the "a" key on its own does in fact produce the Cherokee character equivalent to "a". Furthermore, I know that the "g" key is correctly assigned to dead_grave, because if I hit g + i (which I left unassigned for now) I get "ì".

Now my locale is en_US.UTF-8, and since I want to customize the compose sequence, copied the file /usr/share/X11/locale/en_US.UTF-8/Compose file to ~./XCompose, which is supposed to OVERRIDE the default compose sequences. In this file, added the following line: 

<dead_grave> <U10013A0>	: "&#5030;" U13A6 # CHEROKEE GA 

(you won't see the Cherokee character in quotes correctly unless you have a Cherokee font installed on your system).

The problem is that the sequence that I defined in ~/.XCompose is not being recognized. In fact, when I switch to my Cherokee layout, g + a produces nothing at all. I've experimented with the .XCompose (as well as the original /usr/.../en_US.UTF-8/Compose file) and discovered that removing certain sequences fails remove these sequences from the keyboard. For example, I've removed all references to the German ß character in both files, but hitting <Multi_key> <s> <s> STILL produces ß. Also, adding things to the file has no effect either. In other words, nothing I do to the compose files seems to have any effect on my ability to CHANGE the default compose settings.

Any help I can get to achieve this goal (which I currently have to use my Mac for) will be greatly appreciated!

Note: I am avoiding the SCIM/KMFL solution because I've found it to be less than reliable. Likewise, I can't use workarounds which involve using compose/shift/ctrl/alt combinations. These are great for occasionally having to enter non-standard characters, but are extremely tedious for writing a whole paragraph purely in Cherokee. I need to be able to assign multiple dead keys on the keyboard such that I can type "gedo dejadoa" and get as output the five Cherokee characters (plus space) that make up this phrase).

---

### Post by haldrik on 2008-11-11
bump

---

### Post by haldrik on 2008-11-26
This is such a surprise to me: no one at Experts Exchange was able to figure this out either. Guess I'll keep waiting....

---

### Post by &#5097;&#5103;waya on 2008-12-28
Have you made any progress on this?

---

### Post by &#5097;&#5103;waya on 2009-01-03
I can report SUCCESS!

> 
assign multiple dead keys on the keyboard such that I can type "gedo dejadoa"

&#5032;&#5081; &#5077;&#5091;&#5081;&#5024;

Do the following:

```
sudo im-switch -s default-xim
```

Put the following file into ~/.XCompose :

(quoted inline and attached as .XCompose.txt)

log off
log on
use the keyboard switch applet, switch to the US-Cherokee Variant keyboard.
 
typed | result:
---------------
tsalagi | &#5091;&#5043;&#5033;
osiyo | &#5027;&#5071;&#5106;
tsiSdu | &#5093;&#5069;&#5082;

Syllabary First Row:
a &#5024;
e &#5025;
i &#5026;
o &#5027;
u &#5028;
v &#5029;

```

# ~/.XCompose
# This file defines custom Compose sequences for Unicode characters

# Import default rules from the system Compose file:
include "/usr/share/X11/locale/en_US.UTF-8/Compose"

#a -> v
<U13A0> :	"&#5024;" #a
<U13A1> :	"&#5025;" #e
<U13A2> :	"&#5026;" #i
<U13A3> :	"&#5027;" #o
<U13A4> :	"&#5028;" #u
<U13A5> :	"&#5029;" #v

#ga -> gv
<U13A6><U13A0>: "&#5030;" #ga
<U13B8><U13A0>: "&#5031;" #ka
<U13A6><U13A1>: "&#5032;" #ge
<U13A6><U13A2>: "&#5033;" #gi
<U13A6><U13A3>: "&#5034;" #go
<U13A6><U13A4>: "&#5035;" #gu
<U13A6><U13A5>: "&#5036;" #gv

#ha -> hv
<U13AF><U13A0>: "&#5037;" #ha
<U13AF><U13A1>: "&#5038;" #he
<U13AF><U13A2>: "&#5039;" #hi
<U13AF><U13A3>: "&#5040;" #ho
<U13AF><U13A4>: "&#5041;" #hu
<U13AF><U13A5>: "&#5042;" #hv

#(la)
<U13B5><U13A0>: "&#5043;" #la
<U13B5><U13A1>: "&#5044;" #le
<U13B5><U13A2>: "&#5045;" #li
<U13B5><U13A3>: "&#5046;" #lo
<U13B5><U13A4>: "&#5047;" #lu
<U13B5><U13A5>: "&#5048;" #lv

#(ma)
<U13C5><U13A0>: "&#5049;" #ma
<U13C5><U13A1>: "&#5050;" #me
<U13C5><U13A2>: "&#5051;" #mi
<U13C5><U13A3>: "&#5052;"  #mo
<U13C5><U13A4>: "&#5053;" #mu

#(na)
<U13BE><U13A0>: "&#5054;" #na
<U13BE><U13BB><U13A0>: "&#5055;" #hna
<U13BE><U13CC>: "&#5056;" #nah/(typed: nA)
<U13BE><U13A1>: "&#5057;" #ne
<U13BE><U13A2>: "&#5058;" #ni
<U13BE><U13A3>: "&#5059;" #no
<U13BE><U13A4>: "&#5060;" #nu
<U13BE><U13A5>: "&#5028;" #nv

#(qua)
<U13AA><U13A4><U13A0>: "&#5062;" #qua
<U13AA><U13A4><U13A1>: "&#5063;" #que
<U13AA><U13A4><U13A2>: "&#5064;" #qui
<U13AA><U13A4><U13A3>: "&#5065;" #quo
<U13AA><U13A4><U13A4>: "&#5066;" #quu
<U13AA><U13A4><U13A5>: "&#5067;" #quv

#(sa)
<U13CD><U13A0>: "&#5068;" #sa
<U13CE>: "&#5069;" #s / (typed S)
<U13CD><U13A1>: "&#5070;" #se
<U13CD><U13A2>: "&#5071;" #si
<U13CD><U13A3>: "&#5072;" #so
<U13CD><U13A4>: "&#5073;" #su
<U13CD><U13A5>: "&#5074;" #sv

#(da)
<U13D7><U13A0>: "&#5075;" #da
<U13D4><U13A0>: "&#5076;" #ta
<U13D7><U13A1>: "&#5077;" #de
<U13D4><U13A1>: "&#5078;" #te
<U13D7><U13A2>: "&#5079;" #di 
<U13D4><U13A2>: "&#5080;" #ti
<U13D7><U13A3>: "&#5081;" #do
<U13D7><U13A4>: "&#5082;" #du
<U13D7><U13A5>: "&#5083;" #dv

#(dla)
<U13D7><U13B5><U13A0>: "&#5084;" #dla
<U13D4><U13B5><U13A0>: "&#5085;" #tla
<U13D4><U13B5><U13A1>: "&#5086;" #tle
<U13D4><U13B5><U13A2>: "&#5087;" #tli
<U13D4><U13B5><U13A3>: "&#5088;" #tlo
<U13D4><U13B5><U13A4>: "&#5089;" #tlu
<U13D4><U13B5><U13A5>: "&#5090;" #tlv

#(tsa)
<U13D4><U13CD><U13A0>: "&#5091;" #tsa
<U13D4><U13CD><U13A1>: "&#5092;" #tse
<U13D4><U13CD><U13A2>: "&#5093;" #tsi
<U13D4><U13CD><U13A3>: "&#5094;" #tso
<U13D4><U13CD><U13A4>: "&#5095;" #tsu
<U13D4><U13CD><U13A5>: "&#5096;" #tsv

#(wa)
<U13B3><U13A0>: "&#5097;" #wa
<U13B3><U13A1>: "&#5098;" #we
<U13B3><U13A2>: "&#5099;" #wi
<U13B3><U13A3>: "&#5100;" #wo
<U13B3><U13A4>: "&#5101;" #wu
<U13B3><U13A5>: "&#5102;" #wv

#(ya)
<U13EF><U13A0>: "&#5103;" #ya
<U13EF><U13A1>: "&#5104;" #ye
<U13EF><U13A2>: "&#5105;" #yi
<U13EF><U13A3>: "&#5106;" #yo
<U13EF><U13A4>: "&#5107;" #yu
<U13EF><U13A5>: "&#5108;" #yv

#remap numbers and symbols back to US English use.
# `: "`"
# 1: "1"
# 2: "2"
# 3: "3"
<U13D9>: "4" # &#5081;4
<U13E6>: "5" # &#5094;5
<U13DC>: "6" # &#5084;6
<U13CB>: "7" # &#5067;7
<U13D6>: "8" # &#5078;8
<U13D2>: "9" # &#5074;9
<U13C4>: "0" # &#5060;0
<U13BF>: "-" # &#5055;-
<U13F3>: "=" # &#5107;=

<U13CA>: "~" #&#5066;~
<U13B1>: "!" #&#5041;!
<U13C7>: "@" #&#5063;@
<U13E7>: "#" #&#5095;#
<U13B0>: "$" #&#5040;$
<U13B9>: "%" #&#5049;%
<U13DD>: "^" #&#5085;^
<U13E1>: "&" #&#5089;&
<U13BA>: "*" #&#5050;*
#(: "("
#): ")"
<U13BC>: "_" #&#5052;_
<U13BD>: "+" #&#5053;+

<U13D5>: "[" #&#5077;[
<U13B6>: "]" #&#5046;]
<U13C0>: "\\" #&#5097;&#5097;\

<U13D1>: "{" #&#5073;{
<U13E4>: "}" #&#5092;}
<U13EE>: "|" #&#5102;|

<U13E8>: ";" #&#5096;;
#': "'"

<U13E0>: ":" #&#5088;:
#": "\""

#,: ","
#.: "."
<U13C2>: "/" #&#5058;/

<U13E2>: "<" #&#5090;<
<U13B4>: ">" #&#5044;>
<U13C9>: "?" #&#5065;?


```


> **haldrik said:**
> Hello:

I'm trying to set up my keyboard to use dead keys to input Cherokee letters (unicode 13A0-13F4) in Ubuntu Gutsy. Here is what I want to do exactly. I want to be able to switch to my custom Cherokee layout and type a consonant (assigned as one of the already existing dead keys) + a vowel key to get the corresponding Cherokee character (which represents the whole syllable). Once I get this exact method to work for ONE combination (lets say "g" plus "a" makes Cherokee "GA"), I'm sure I can get the whole keyboard customized. Here's what I've done: 

First, I've universally changed the input method to "xim".

Then, I added a new keyboard layout in /usr/share/X11/symbols/us, such that, among many other assignments, the "g" key is assigned to "dead_grave" and the "a" key (<AC01>) is assigned to the Cherokee vowel A. ( Here are the relevant lines from that file):

key <AC01> { [ 0x10013A0,  a,  	A,  A ] };
key <AC05> { [ dead_grave, g,	G,  G]  };

(When I use this keyboard layout, the "a" key on its own does in fact produce the Cherokee character equivalent to "a". Furthermore, I know that the "g" key is correctly assigned to dead_grave, because if I hit g + i (which I left unassigned for now) I get "ì".

Now my locale is en_US.UTF-8, and since I want to customize the compose sequence, copied the file /usr/share/X11/locale/en_US.UTF-8/Compose file to ~./XCompose, which is supposed to OVERRIDE the default compose sequences. In this file, added the following line: 

<dead_grave> <U10013A0>	: "&#5030;" U13A6 # CHEROKEE GA 

(you won't see the Cherokee character in quotes correctly unless you have a Cherokee font installed on your system).

The problem is that the sequence that I defined in ~/.XCompose is not being recognized. In fact, when I switch to my Cherokee layout, g + a produces nothing at all. I've experimented with the .XCompose (as well as the original /usr/.../en_US.UTF-8/Compose file) and discovered that removing certain sequences fails remove these sequences from the keyboard. For example, I've removed all references to the German ß character in both files, but hitting <Multi_key> <s> <s> STILL produces ß. Also, adding things to the file has no effect either. In other words, nothing I do to the compose files seems to have any effect on my ability to CHANGE the default compose settings.

Any help I can get to achieve this goal (which I currently have to use my Mac for) will be greatly appreciated!

Note: I am avoiding the SCIM/KMFL solution because I've found it to be less than reliable. Likewise, I can't use workarounds which involve using compose/shift/ctrl/alt combinations. These are great for occasionally having to enter non-standard characters, but are extremely tedious for writing a whole paragraph purely in Cherokee. I need to be able to  and get as output the five Cherokee characters (plus space) that make up this phrase).

---

### Post by TheProphetJonah on 2009-12-18
Hey howdy. I'm trying to put together a Unix version of a Dos-ish program called Cherokee Companion, which is a tutorial for Sikawi's Syllabary.

Since I don't have the faintest idea as to what the Hell I'm doing, it's an interesting project.

I know there's an actual layout comes canned with Ubuntu 9.10 for Cherokee, and that somehow, some way, Orca and Speex and Festival (probably using the same engine) support it. Plus Cherokee Companion has a really clear voice pronouncing the Syllabary, but I would need to put it into All Open Source in order to even work on it, much more put out a finished product.

My thought on it is, that the components already exist in Klavaro and ktouch typing tutorials, since they both supposedly port to orca.

I've also got an Idea for promoting the language (10% of all Cherokee people actually speak the language, as opposed to 1860 when only 10% DID NOT speak it.. an exact reverse proportion)

... only, since I'm not even fluent in my first second and third languages, English, Spanish and French, and only know (so far) a few place names in Cherokee ...

But I was on a city bus in Texas translating for a lady who didn't speak much English, and some smart-mouth Redneck demanded she and I should both speak Only English in His Royal Presence. 

Which leads to the idea... A tee-shirt, posters and bumper stickers which say, in Cherokee, "This is America, learn to speak American".

I believe it could promote positive discussions on the issues of racial, cultural and linguistic tolerance in America. 

Problem being I still don't know how to write out myself. I don't even know if there IS a Cherokee place-name for America. It would probably (but I'm not sure) have to be worked out to a phonetic pronunciation. 

Which works on a lot of levels, America is a Spanish corruption of the Italian misspelling of a Portuguese name of a mapmaker who had never been to America in the first place. "Amerigo Vespucci".

How I found THIS thread, and maybe this question would be moved to a whole separate thread, was through my sort of/kind of almost scheduled google searches for anybody who could possibly help develop both concepts.

The Linux open-source tutorial for learning Cherokee and, the tee-shirt idea for promoting the learning Renaissance (french for "rebirth") of the Cherokee Language.

If I have the Cherokee spelling of the phrase, I could use orca or some other speech engine to get the pronunciation right. Sikawi was a freakin' Genius, in my humble opinion, by devising a way of writing a language using symbols that actually phonetically pronounce the language.

It helps greatly, I think, maybe, that we're at least together on the Ubuntu distribution part. Most of the people I wrote to about the project don't know Linux, or don't know Cherokee.
 It needs to be both, yes? 
For whatever help you can give...
Thank you in advance.
Jonah.

---

