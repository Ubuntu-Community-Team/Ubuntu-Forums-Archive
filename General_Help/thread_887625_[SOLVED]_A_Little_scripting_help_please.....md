---
title: "[SOLVED] A Little scripting help please...."
date: 2008-08-12
forum: General Help
---

### Post by WallyWest on 2008-08-12
Hello,
I had trouble finding a bash forum so i thought id take a shot here.
 Could anyone help me with this peice of code? I used aptitude to get the zenity package here.

choice=5

SwitchArray[1]="192.168.118.23"
SwitchArray[2]="192.168.118.10"

SwitchArray[3]="192.168.118.11"

SwitchArray[4]="192.168.118.12"

SwitchArray[5]="192.168.118.13"

ans=$(zenity  --list  --text "Select an IP" --radiolist  --column "Pick" --column "IP address" [COLOR="Red"]${SwitchArray[*]}[/COLOR]); 
echo $ans

The red is what i would like to happen but am obviously not stating correctly. I would like zenity to display each of the IP's in the array as a selectable option.
Sorry if this should be posted elsewhere and if so I will take it down
THanks

---

### Post by koenn on 2008-08-12
There's 2 things wrong with your statement:
1- to get all values from an array (in bash) : ${arr[@]]}
2- the way you wrote it, you're not giving values for the first column (radio buttons: TRUE, FALSE), and apparently zenity needs those


Here's a workaround. I'm not familiar with zenity so I don't know the canonical way to do this.

```

arr= ( 192.168.1.1 192.168.1.2 192.168.1.3 )

ans=$(zenity --list --text "Select an IP" --radiolist --column "Pick" --column "IP address" $(for i in ${arr[@]}; do echo FALSE $i; done) ); 

echo $ans

```

---

### Post by WallyWest on 2008-08-12
> **koenn said:**
> There's 2 things wrong with your statement:
1- to get all values from an array (in bash) : ${arr[@]]}
2- the way you wrote it, you're not giving values for the first column (radio buttons: TRUE, FALSE), and apparently zenity needs those


Here's a workaround. I'm not familiar with zenity so I don't know the canonical way to do this.

```

arr= ( 192.168.1.1 192.168.1.2 192.168.1.3 )

ans=$(zenity --list --text "Select an IP" --radiolist --column "Pick" --column "IP address" $(for i in ${arr[@]}; do echo FALSE $i; done) ); 

echo $ans

```

Thanks... I was actually thinking of exactly that because i also don't know zenity very well at all. But i am also only a few weeks old and self instructed with Linux so its kind of a boondogle trying to teach myself basic shell logic. Im hoping it all comes together soon and the logic will be there enough that i can have basic for loops and such under my belt.
THanks for the advice

---

### Post by WallyWest on 2008-08-12
Well I tried that but it seems that zenity isn't accepting that for loop the same way the shell does. I have successfully passed zenity a variable but it's still unclear to me how to tell zenity to read and display each value in an array. There must be some proprietary command for such a thing. But the zenity man isn't showing anything of the sort.

---

### Post by koenn on 2008-08-12
> **WallyWest said:**
> Well I tried that but it seems that zenity isn't accepting that for loop the same way the shell does. 

zenity never sees that loop/ The way Linux shells work, the shell will execute the loop, resulting in a string that is passed to zenity as values for the radio buttons. 

Here's me doing it: (attached image)

---

### Post by kaibob on 2008-08-12
Koenn's code works fine for me, although I did have to remove the space after arr=.

The following also seems to work for me when tested in a terminal window:

> ans=$(zenity  --list  --text "Select an IP" --radiolist  --column "Pick" --column "IP address" TRUE 192.168.118.23 FALSE 192.168.118.10 FALSE 192.168.118.11 FALSE 192.168.118.12 FALSE 192.168.118.13); echo $ans

---

### Post by WallyWest on 2008-08-14
> **koenn said:**
> zenity never sees that loop/ The way Linux shells work, the shell will execute the loop, resulting in a string that is passed to zenity as values for the radio buttons. 

Here's me doing it: (attached image)

Hey thanks a lot. I forgot to check back and ended up borrowing a book from someone about bash and figured the same thing. I should really get into a class or something instead of having to scramble for answers like this all the time. Thanks for the help though I appreciate it.
THanks,
Tim

---

### Post by decoherence on 2008-08-14
> **WallyWest said:**
> But i am also only a few weeks old and self instructed with Linux...

My god they start 'em early these days!:lolflag:

---

### Post by WallyWest on 2008-08-14
haha
nice catch.

---

