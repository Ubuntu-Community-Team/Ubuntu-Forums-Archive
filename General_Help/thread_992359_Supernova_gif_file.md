---
title: "Supernova gif file"
date: 2008-11-24
forum: General Help
---

### Post by wikibox on 2008-11-24
hello everyone

my question is rather simple in origin
back in 2005 when i still used windows  (ergh!)
once I loaded a beautifully designed key generator that did not have any window frames the logo of the cracker house was just there in the middle almost as a borderless hovering disk and I believe it was just a gif-png-animated  file,now in 2008  I am using ubuntu and for an art project that depicts supernovae and galaxies i would like to replicate the effect so that the celestial masses can slowly turn without any black edges (hope I am conveying the concept clearly)

Is there anyway to create borderless animated gif/pngs files so that they can be freely placed/resized around the screen?

your help is much appreciated

---

### Post by loomsen on 2008-11-24
Yeah, actually it's pretty easy.
You may write a *.xml file specifying which pic when to show.
First, set current time:
```

  <starttime>
    <year>2008</year>
    <month>11</month>
    <day>25</day>
    <hour>01</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>

```
Then specify what should happen, and how long. You may either use static images or "dynamic" ones, which aren't static but transitional.
For the last you can specify how the images should be morphed one into the other.
Duration is for both of these options, so xml style you could do sth like:
```

<static>
<duration>600.0</duration>   <!-- given in seconds, so this would last 10 minutes for instance !-->
<!-- now what should be shown: !-->
<file>/path/to/any/file/foobar-1.png</file>
</static>

```

Transitional images look similar:
```

<transition type="overlay">  <!-- type to use for transformation !-->
<duration>600.0</duration>
<from>/path/to/any/file/foobar-1.png</from>
<to>/path/to/any/file/foobar-2.png</to>
</transition>

```

Now put the file together how you'd like, and tell the system what it actually specifies, by using:
(Comments in blue, obv)
```

<background>

[color=blue]<!-- when to start: !--> [/color]
<starttime>
    <year>2008</year>
    <month>11</month>
    <day>25</day>
    <hour>01</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
     
     <static>
     <duration>600.0</duration>  [color=blue] <!-- given in seconds, so this would last 10 minutes for instance !-->
     <!-- now what should be shown: !--> [/color]
     <file>/path/to/any/file/foobar-1.png</file>
     </static>

     <transition type="overlay">  [color=blue]<!-- type to use for transformation !-->[/color]
     <duration>600.0</duration>
     <from>/path/to/any/file/foobar-1.png</from>
     <to>/path/to/any/file/foobar-2.png</to>
     </transition>

[color=blue]<!-- let's finish this !-->[/color]
</background>

```

Now you have a valid xml file you can simply drag and drop to your appearance dialogue. Just make sure the images are actually located in the path you specified, and enjoy the ride :) Gotta love .xml don't you :)

---

### Post by wikibox on 2008-11-26
dear Loomsen

Man,  i just have one thing tosay : 

thank you thank you an thank you 
i definitely have to study how to use xml files but definitely you have cleared a boulder size blunder....Let me experiment around and see if i can get it to work


many thanks man!!

---

