---
title: "CD burner"
date: 2005-11-09
forum: General Help
---

### Post by woopud on 2005-11-09
For some reason I can't burn cd's, serpentine just keeps going and going for hours and Gnomebaker gives some errors.  Is there another CD burning program out there ?

Bert

---

### Post by jonzep on 2005-11-09
you could try k3b...

---

### Post by StefanoCole on 2005-11-11
I also was not able to burn an audio CD (i.e. to put wav files in it) neither with Serpentine nor with Gnomebaker (indeed with Hoary and Gnomebaker I was able). So, from command line I tried cdrecord:

$ cdrecord dev=/dev/hdc *.wav

and I was successful. Note: my cd burner is /dev/hdc

Bye bye, Stefano

---

