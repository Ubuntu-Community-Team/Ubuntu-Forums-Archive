---
title: "[SOLVED] converting filenames between encodings not working with convmv"
date: 2008-08-15
forum: General Help
---

### Post by kung fu buntu on 2008-08-15
I have downloaded a .rar file but have found the filenames inside completely messed up.
My system is set to en_US.UTF-8

I have tried using convmv with several encodings (all of iso-*) but had no luck :(

$convmv -f iso-8859-1   -t utf8    *
mv "./Ant&#65533;nio Varia&#65533;&#65533;es.txt" "./Ant¢nio Variaäes.txt"
$convmv -f iso-8859-15  -t utf8    *
mv "./Ant&#65533;nio Varia&#65533;&#65533;es.txt" "./Ant¢nio Variaäes.txt"


I know how the correct filename should be like (António Variações). Is there any way to given a mapping the bad encoding is detected and the correct one is set?
I haven't tried any cp* encoding... since I think that's for asian languages, or am I wrong?

Thank you.




EDIT:
hrrmmrmrmmmr.... I hate when this happens... I spend lots of time searching for something without finding an answer and then post a question somewhere. Then give it one more try and it works :/
I found the correct encoding for the bad filenames, it's cp850.

---

