---
title: "Calculator 100 -42% 99.58?"
date: 2008-11-17
forum: General Help
---

### Post by pcjunkie on 2008-11-17
Am I the only one getting this?

If I put 100 - 42% in the calculator I get 99.58 return?

major bug?

---

### Post by RequinB4 on 2008-11-17
It's not a bug, 42% is .42, 100 - .42 = 99.58

Check your math :P

---

### Post by sirjoebob on 2008-11-17
SOLVED. lol

---

### Post by ibuclaw on 2008-11-17
I'll give you a hint...

BODMAS

Think about the order of which the calculator solves the problem:
```
100-42%
```
If that wasn't enough, the above equates to:
```
100-42/100
```
Which in turn equals
```
100-0.42
```

So you should be putting in your **B**rackets :P

```
(100 - 42)%
```

Regards
Iain

---

### Post by pcjunkie on 2008-11-17
lol interesting..

I have a 10 dollar calculator and it gives the correct answer

58...

---

### Post by sirjoebob on 2008-11-17
> **pcjunkie said:**
> lol interesting..

I have a 10 dollar calculator and it gives the correct answer

58...

Define correct..... :lolflag:

Google search "100-42%":
	
100 - (42%) = 99.58

This is technically correct for how it is input.

---

### Post by pcjunkie on 2008-11-17
Well ok screw google

100 is 100

42% is 42 out of 100 = 42

100 subtract 42 = 58

10% of 100 = 10 = 90  

20 % of 100 = 20 = 80

etc etc etc///

BODMAS is too pedantic for a little we calculator yes?

Windows cals gives 58
10 dollar calc gives 58
math on paper gives 58 (no bodmas)
why does gnome calc need Bodmas for such a simple sum?

---

### Post by ibuclaw on 2008-11-17
Mechanical calculators work slightly different.

When you hit the % button, it actually performs a certain function.

1) =
2) ANS / 100


With GCalc though, % is interpreted as part of the same line, and the line is not executed **until** you press "**=**" or the Enter key.

So this isn't a bug... it's a technical feature ;)

Regards
Iain

---

### Post by sirjoebob on 2008-11-17
42% without a definition of the whole is just .42

---

### Post by ibuclaw on 2008-11-17
> **pcjunkie said:**
> Well ok screw google

100 is 100

42% is 42 out of 100 = 42

100 subtract 42 = 58

10% of 100 = 10

20 % of 100 = 20

etc etc etc///

Since when did you ever define "42%" as being out of 100 ?

42% means nothing on it's own in terms of what number that percentage is out of.

if you had
```
100-100*42%
```
Then you'd get your answer.

Regards
Iain

---

### Post by RequinB4 on 2008-11-17
This is a feature of any higher level calculator that allows you to input complex formulas.

Under a basic four function calculator (like your 10 dollar one) the computer processes as follows:

Type 100
enter
(answer) minus 45
enter
(answer) as a percent

thus you get 100 - 45 = 55, 55% = .55

In any other calculator, you compute it all at at time because you can edit the line before you input.

Think that's a bad feature?  try computing ln((55 - 4)^4)(45^2 + -45)) by four function calculator and see what's faster.

learn order of operation :P

---

### Post by issih on 2008-11-17
I'm with everyone else...per cent means parts of 100. so 42%  is 42/100 = 0.42

Thats the definition of percent, its how it works

---

### Post by pcjunkie on 2008-11-17
Well I just found it interesting. Any other calc does it simply..

and percent is n/100 yes?

I can see this tripping up people who are used to simple equations getting correct answers without the need for more than elementary entry level mathematics...


what 6 year cant do 100/100

what 6 year old will understand BODMAS principles?

So if using the Gnome calc (yes its a wonderful thing and texas instruments would be proud of it.) 

one should understand it needs higher level math methods to get it to work for a boffin...

---

### Post by poebae on 2008-11-17
> **tinivole said:**
> Since when did you ever define "42%" as being out of 100 ?

42% means nothing on it's own in terms of what number that percentage is out of.
Actually, 42% by definition means 42/100

per cent = out of hundred

---

### Post by pcjunkie on 2008-11-17
I just mucked around a bit with it and found it used BODMAS on all settings even financial.

this can trip people people up...like me..:)

---

### Post by karlr42 on 2008-11-17
BOMDAS is basic mathematics. It's fundamental if you're going to be using multiple operators in the same expression(like here). You should all know it if you went to high school(I'm not American, so don't know if that's the right stage), I learned it at 13, I think, but quite possibly earlier.

---

### Post by ibuclaw on 2008-11-17
BODMAS is a simple concept.

I learned it when I was 8...

And besides, it's not exactly hard to remember ;)

**B**rackets
p**O**wers
**D**ivision
**M**ultiplication
**A**ddition
**S**ubstraction

[EDIT]
Straight from the manual:
```

**Function      Button   Description                        Example  Result**
Percentage    %        Divides the current value by 100.  560 % =  5.60

```

Regards
Iain

---

### Post by spiderbatdad on 2008-11-17
I have a problem calculating the reciprocal of the sum of several reciprocals with gnome calc. If I press 5 and 1/x + 5 and 1/x + 5 and 1/x = and 1/x = I do not get the recip of 5 plus the recip of 5...instead... the recip of the recip of 5 +5...

---

### Post by ncanna1 on 2008-11-17
But the problem is that you are wanting to subtract 48% from the whole number 100.  If you wanted it to behave in the way that you are describing, then you would want to use 100% - 48%, which is .52 .  However, the way that you are doing it makes the calculator process 100/1 - 48/100 = 99.52.

---

