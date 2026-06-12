---
title: "what else can i do with linux"
date: 2008-07-23
forum: General Help
---

### Post by kielanmatt on 2008-07-23
i got internet working on it then i got ICS for my xbox360

i got WoW running on it and i am a maintainer of 3 apps on AppDB.wine and i got one game working AND i installed Beryl

currently im trying to get my XBox360 Headset working but apart from that there is nothing challenging to do i used to have an interactive radio station on shoutcast but if i were to do it now i would have to write a program to controll XMMS playback etc. and i dunno how to make one.

the thing is that i am very advenced with computing in general but i cant build apps (i tried several times but i gave up) all i ever did is networking&website design and solving sime driverloading when i got errors

tell me what can i do (keep in mind im only 13)

---

### Post by kielanmatt on 2008-07-23
Tell me please!!!!!!!!!!!!1

---

### Post by ad_267 on 2008-07-23
Maybe learn how to make gtk themes or emerald or metacity themes. Have a look at gnome-look.org.

You could learn to write basic scripts in python.

---

### Post by kielanmatt on 2008-07-24
i learned and re-invented the prime number script before getting to section 4.4 on python.org tutorial i re worked it and i think it works (i tried with the first 100 primes and ok)

This is it

```
# Finding prime numbers using a computer Erastothenes or summink like that sieve
f = 11 #f will be a very important value
ged = 16 #i can't be bothered to let the computer test 15 lower numbers so i start with 16
print ('2,3,5,7,11,13') # due to the construction of this script the first 6 primes are not
#written
while ged < 5000: #highest number to test
	f = 11 #make sure that f equals 11 after the second WHILE statement BREAKS
	if ged/2 == (ged-1)/2: # filters out any even numbers
		if ged/3 == (ged-1)/3: # clears any multiplies of three
			if ged/5 == (ged-1)/5: # any numbers ending with 0 or 5
				if ged/7 == (ged-1)/7: # any multiplies of 7, this is done
# so there is less calculations in the loop below
					while f <= ged: # there is no point in having the
# divisor "f" higher than the dividend "ged"this loop is not very processor efficient
# because it makes a lot of calculations
						if ged/f == (ged-1)/f: # if ged is a
# multiple of f the answear to (ged-1)/f will be lower by 1 and get redirected to f = f+2
							if f == ged: # no point to this
# function its here just to get the else function ELSE beneath working
								print (ged) # prints ged
								ged = ged+1 # makes ged
# higher by 1 so the next number gets tested
								break # breaks the loop and
# returns to the first loop
							else:
								f = f+2 # if f is lower than
# ged AND ged is not the multiple of f, the next line adds 2 to f. This is because there is
# no use in having the divisor an even number, line 6 does the job already
						elif f == ged: # does same as IF 5 lines
# above but if i were to delete that one the process would freeze at number 113
							print (ged) # prints ged
							ged = ged+1 # makes ged higher
							break # breaks the loop
						else: # if ged/f == (ged-1)/f OR f == ged do
# not apply
							ged = ged +1 # makes ged higher
							break # breaks the loop
				else: # if the number tested "ged" is a multiple of 7
					ged = ged+1 # repeat the loop with ged higher by 1
			else: # if ged is a multiple of 5
				ged = ged+1 # start again with a higher number
		else: # if ged is a multiple of 3
			ged = ged+1 # start again with ged higher
	else: # if ged is a multiple of 2 /even number
		ged = ged+1 # start again
#im currently working on a script that tests only one specified number, but i have to get to
#know the INPUT command
# copyright matthew kielan 2008
```

Im soo proud i made it (Im 13 :)) i know its not a big achievement

---

### Post by iDaniel on 2008-07-24
My first suggestion would be to start learning your way around [bash]("http://www.google.com/search?q=bash+tutorials&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a").

It's an extremely invaluable tool and it's good to learn if you want to begin to use linux to its full potential.

---

### Post by scragar on 2008-07-24
hmn, couldn't you make it more efficient by using an array to store primes, then test if each number is a multiple of any of the primes, if it's not then it's a prime.

example bellow in perl, I don't know python, but it can't be hard to understand.
```
[b]#!/usr/bin/env perl
# line above is the shebang, if you don't know what that is go google it.[/b]


sub isprime {**# first a function, returns true if a numbers prime, as well as adding it to the list of primes.**
  my($possible, $cur) = @_;**# who cares if $cur is now a defined var with undefined as a value, it improves performance, just don't enable strict**
  foreach $cur (@primes){**# for each prime**
    return 0 if !($possible % $cur); **# exits returning false if number is a multiple**
  }
  push(@primes, $possible);**# add to list**
  return 1;
}

@primes =(2, 3);**# start of list of primes, 2 and 3 is a good start :P**
for($i = 5; $i < 500; $i++){**# change 500 to whatever max prime can be**
  isprime($i);**# test if it's a prime**
}
print "@primes\n";**# print list of primes.**
```
the bold bits are comments BTW, just so they stand out.

---

### Post by kielanmatt on 2008-07-25
i dont get that at all, i think i stick to python

---

### Post by kielanmatt on 2008-07-25
i think pearl and python same time is a bit too much for a 13 year old

---

### Post by scragar on 2008-07-25
it was only an example of what I belived to be a more efficient method, you don't need to learn perl to be able to read the code, that's why I put so many comments on.

pseudocode any help(pseudocode = steps of code written as english)?
```
make a list of starting prime numbers
loop through all numbers up to the max
  loop through all the primes in the list
     if the prime is a multiple of the number quit back to next set of first loop
  end loop
  add number to list if there wasn't any multiples
end loop
show lists so far.
```

---

### Post by houbysoft.xf.cz on 2008-07-25
hehe :) make your own website! :) like me :) (I'm 14 :))

---

### Post by Orlsend on 2008-07-25
Python is Cool, Pearl... nah

yeah why wont try to make a site?

Lern some Php or html, or simply fool around with CMS

---

### Post by Orlsend on 2008-07-25
Sorry My FF resended data by it's own

---

### Post by kielanmatt on 2008-07-25
i did that already devushwebs.cba.pl i dunno if its still running

---

