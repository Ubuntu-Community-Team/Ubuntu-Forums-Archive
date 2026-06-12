---
title: "gdesklets"
date: 2004-10-16
forum: General Help
---

### Post by eNiNjA on 2004-10-16
I have been trying to get this to run with no luck at all.

I installed it like so:

sudo apt-get install gdesklets

I downloaded GoodWeather, and did the following:

cd mydesklets/GoodWeather

./Install_GoodWeather_Sensor.bin

It tells me it is installed, and I can now use it.

Now I issue the following commands: (still in the GoodWeather directory)

gdesklets

gdesklets open GoodWeather.display

It outputs:

Could not add display
The display could not be added because the file does not exist.

Am I overlooking something simple? (probably)

---

### Post by eNiNjA on 2004-10-17
hmmmm...nobody

eninja@parts-unknown ~ $ sudo apt-get remove gdesklets

hehe...

---

### Post by rupert on 2004-10-17
use gdesklets GoodWeather.display
the version on the repo is older than the ones in the howtos.

---

### Post by eNiNjA on 2004-10-18
yup, that did it, thanks  :D

---

