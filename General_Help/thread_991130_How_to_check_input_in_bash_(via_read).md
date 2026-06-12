---
title: "How to check input in bash (via read)?"
date: 2008-11-23
forum: General Help
---

### Post by jakonj on 2008-11-23
im trying to create agenda in bash but there is one thing that i dont now how to solve. Here is an example:
```
datum="[0-3][0-9]-[0-1][0-9]-[0-9][0-9][0-9][0-9]"

echo "Unesite datum obaveze (dan-mesec-godina (primer: 21-12-2008)): "; read obaveza

while [ "$obaveza" != $datum ]
do
echo "GRESKA: Datum obaveze nije unet u ogovarajucem formatu!"
echo "Unesite datum obaveze (dan-mesec-godina (primer: 21-12-2008)): "; read obaveza
done

```

Since i need correct date in $obaveza i need to check that input but there is error. I dont now how to solve it and i belive that my code is not good so can somebody help me?

What i need:
1. read $obaveza
2. Compare $obaveza with $datum (in $datum i use range of numbers and they are representing DD-MM-YYYY)
3. If there is no "good" input you need to try again.

Thanks :)

---

### Post by __Ryan__ on 2008-11-23
I'm sure there is a more elegant solution but this will work.

```
datum="[0-3][0-9]-[0-1][0-9]-[0-9][0-9][0-9][0-9]"

echo "Unesite datum obaveze (dan-mesec-godina (primer: 21-12-2008)): "; read obaveza

while [ 0 == $(echo "$obaveza" | grep "$datum" | wc -l) ]
do
echo "GRESKA: Datum obaveze nije unet u ogovarajucem formatu!"
echo "Unesite datum obaveze (dan-mesec-godina (primer: 21-12-2008)): "; read obaveza
done
```

---

### Post by jakonj on 2008-11-24
Works for me.
Thank you Ryan :)

---

