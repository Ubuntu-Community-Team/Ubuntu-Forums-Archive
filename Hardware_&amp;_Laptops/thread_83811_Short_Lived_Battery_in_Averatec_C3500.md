---
title: "Short Lived Battery in Averatec C3500"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by Plank117 on 2005-10-29
I've a fine laptop computer with an annoying problem: in Linux its sucks batteries dry pretty damn fast. How do I fix this? Is there any sort of power saving utility available? I'm sick of having to use windows when I'm working somewhere where there isn't an  outlet or plugging in is just not an option. Generally, if I'm doing something on my computer in a less than ideal location, it's pretty damn important. Windows has a knack for failing during critical tasks. Help would be very appreciated.

---

### Post by res_overlord on 2005-10-30
How long is the battery lasting?  According to this review:

[http://www.hardwarecentral.com/hardwarecentral/reviews/5650/2/](http://www.hardwarecentral.com/hardwarecentral/reviews/5650/2/)

You should not expect more than an hour and a half.

Also, check to see if your processor is scaling down.  If it is constantly running at top speed, you may need to ensure that your cpu downscaling is enabled and working properly.

---

### Post by Plank117 on 2005-10-31
I get an hour and a half under Windows, but Linux will drain the battery in about 45 minutes. How do I enable downscaling? Whenever I boot into Linux it says that my AMD Athlon XP-M does not support power saving.

---

### Post by Plank117 on 2005-10-31
I fixed it by configuring powernowd. I just split the step frequency in half and doubled the battery life. For the sake of posterity, I used this command:
```
sudo powernowd -s 50000
```
The integer at the end is the frequency jump in kHz,  you can substitute any integer you like.

---

