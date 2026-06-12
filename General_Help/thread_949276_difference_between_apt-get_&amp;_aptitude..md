---
title: "difference between apt-get &amp; aptitude."
date: 2008-10-16
forum: General Help
---

### Post by krishna1650 on 2008-10-16
i want to difference between apt-get & aptitude.

---

### Post by iKonaK on 2008-10-16
```
man apt-get
man aptitude
```>  apt-get - APT package handling utility -- command-line interface
>  apt-get is the command-line tool for handling packages, and may be
       considered the user´s "back-end" to other tools using the APT library.
       Several "front-end" interfaces exist, such as dselect(8), aptitude,
       synaptic, gnome-apt and wajig.

       Unless the -h, or --help option is given, one of the commands below
       must be present.
>  aptitude - high-level interface to the package manager
> aptitude is a text-based interface to the Debian GNU/Linux package
       system.

       It allows the user to view the list of packages and to perform package
       management tasks such as installing, upgrading, and removing packages.
       Actions may be performed from a visual interface or from the
       command-line.


---

### Post by pak33m on 2008-10-16
You could also look at [http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude").  This is a visual representation. 

One of the biggest differences other than resolving and removing dependencies is that aptitude provides a text-based installer while apt-get uses the Synaptic program.

---

### Post by Yellow Pasque on 2008-10-16
The difference is in the Super Cow Powers.

> Although aptitude, the successor to apt-get does not have Super Cow powers (typing "aptitude --help" brings up a help screen that informs you of this at the end), it does have an easter egg.
1.Type "aptitude moo" & press ENTER
aptitude responds with "There are no Easter Eggs in this program."
2.Type "aptitude -v moo" & press ENTER
This time, the response is "There really are no Easter Eggs in this program."
3."aptitude -v -v moo" causes it to respond with "Didn't I already tell you that there are no Easter Eggs in this program?"
4."aptitude -v -v -v moo" causes the response "Stop it!"
5.if you add a fourth -v ("aptitude -v -v -v -v moo"), aptitude responds with "Okay, okay, if I give you an Easter Egg, will you go away?"
6.adding a fifth -v "aptitude -v -v -v -v -v moo") causes it to respond with "All right, you win.", followed by a crude, unrecognizable ASCII drawing.
7.putting the -v six or more times ("aptitude -v -v -v -v -v -v") answers the question of what the drawing is - "What is it? It's an elephant being eaten by a snake, of course."
8. this is a reference to Antoine de St. Exupery's "The Little Prince"


---

