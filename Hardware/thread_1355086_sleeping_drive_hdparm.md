---
title: "sleeping drive hdparm"
date: 2009-12-14
forum: Hardware
---

### Post by rzial on 2009-12-14
drive is a samsung HM160HC I have been trying to make this drive sleep when not in use as its in a NAS and I figure sometimes it will be weeks when I do not use it and I do not like the idea of it spinning for long durations when it is not needed

I have set the drive standby to 20 mins with -S  (also used -K 1 to keep features over reset)

this originaly seemed to do nothing as the drive was still spinning hours later so I enabled APM with -B on 1 and then on 126

#1 should be agressive power saving and #126 not so agressive but still spin down higher values will not spin the drive down (or so im told)

 testing both settings the drive seems to make the drive spin down but it does so after abour 3 seconds (im hearing it spin up while browsing through folders somtimes)

I fear this will have the opposite effect and kill my drive lots sooner than I want

Could I be missing some sort of magic command to make it work or will the drive just not support it?

suggestions welcome

Thanks

---

### Post by rzial on 2009-12-14
nm I fixed it (sort of)

first disabled the apm (it wasnt great anyway)
then messed around with different numbers in the timeout option "-S" and randomly tested it with 1 and sure enough after 5 seconds the drive spundown

tested with several numbers below 99 and each time the drive spun down as it should then tested it with a number greater than 99 (think it was 120 or so I dont remember) around 1h:40m later drive is still spinning

It seems hdparm or the drive did not like using numbers greater than 99 after I set it to 99 after 8 min 15 sec drive spins down perfect

would have perfered an hour spindown but its close enough for me

hope this helps anyone else that runs into the problem

Cheers

---

### Post by rzial on 2009-12-15
just a little more info if anyone needs 

after more tinkering I found ubuntu just kept spitting out an error message when sending the save option -k1 i figured it was not supported by the drive 

just had a mess around on a terminal connected to the nas and its version of hdparm was fine sending -k1 to the drive so all sorted now :)

Cheers

---

### Post by kingrolo on 2010-01-10
Thanks for the info..very useful.

I have 2 drives; one spins down as it should with apm=254 and any spindown time. The other behaves just as you describe. I've set apm=255 and it seems ok now. I haven't tried a spindown time above 99.

Is this a bug or a harddisk failure..or a feature?

Thanks again,
Peter.

---

