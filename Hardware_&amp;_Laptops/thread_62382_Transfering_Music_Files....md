---
title: "Transfering Music Files..."
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by xm4r5h4llx on 2005-09-04
Okay here is my problem... I am getting ready to install ubuntu onto my laptop as the primary OS with windows as sort of a back-up or a fall back incase of any major problems... however all my music files are either on my iPod or on my hard drive which at the moment is formatted in ntfs for windows... My question is can I access those files from ubuntu even the ipod because as far as I know the ipod is also formatted with the ntfs format...

any thoughts, questions, or comments? Maybe even a few recomendations as to what to do? I am kinda new to the whole linux scene so forgive me if this is a noobish question...   :razz:  

thanks in advance.

xm4r5h4llx

---

### Post by s_p_a_r_k_y on 2005-09-04
sure you can access ntfs or the ipod, its no big problem, just don't wipe out the NTFS partition during install

---

### Post by xm4r5h4llx on 2005-09-06
okay now i have all my music files on my ipod... although through human error i no longer have the files on my computer...
I can access the files on the ipod however they are all in the acc format and wont play... is there some sort of converter or codec plugin for that file type?
if so how do i get it and install it?

thanks

---

### Post by s_p_a_r_k_y on 2005-09-06
I believe that amarok can play the m4a files. I also wrote a script to convert .m4a files to mp3s.

```

#!/bin/bash
#
# Dump m4a to wav (first step in conversion)

y=`pwd`
cd "$1"

echo changing directory to $1
sleep 15
echo converting the damned .m4as to mp3s
for i in *.m4a
do
mplayer -ao pcm "$i" -aofile "$i.wav"
done

echo converting the damned .wavs to mp3s
for i in *.wav
do
lame -h -b 192 "$i" "$i.mp3"
done

echo renameding the damned mp3s
for i in *.mp3
do
x=`echo "$i"|sed -e 's/m4a.wav.mp3/mp3/'`
mv "$i" "$x"
done

rm *.wav
rm *.m4a
cd $y

echo changing back to $y

```

save that somewhere and make it executable (chmod +x file)
Then run it as ./file path/to/m4as

You'll probably want to copy the m4as from the ipod to the hard drive first, as this script converts and removes the m4as.

---

