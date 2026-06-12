---
title: "can't view my pdf files"
date: 2008-09-04
forum: General Help
---

### Post by jmd9qs on 2008-09-04
hi,

don't know exactley what is going on with my computer, but some of my PDF's won't open in any viewer.... when I try to open with evince, i get this:

```
Unhandled MIME type: “application/octet-stream”
```

the other viewers just say they can't open the file...

any suggestions?

---

### Post by aloshbennett on 2008-09-05
from the mime type, looks like they are some sort of binary file and not pdf. What exactly are these pdfs?

---

### Post by bigbrovar on 2008-09-05
do u have adobe reader .. if not add this to your repo and install it adobe reader from synaptic  ```
 deb http://packages.medibuntu.org/ hardy free non-free
```

---

### Post by jmd9qs on 2008-09-05
these pdf's are books... when i do:
```

file An_Introduction_to_Cosmology.pdf
```

i get:

```
# file An_Introduction_to_Cosmology.pdf
An_Introduction_to_Cosmology.pdf: data
```


so yes, it does look like something weird... can't figure it out

---

### Post by jmd9qs on 2008-09-05
i am installing adobe reader now.... 

will keep you posted as to whether it reads it or not. i would still like to fix this MIME problem though, cause i like evince and am pretty frustrated cause half the books i have in pdf have this error associated with them.

---

### Post by unutbu on 2008-09-05
Type 
```

head An_Introduction_to_Cosmology.pdf
```
it should start with something like```

%PDF-1.3
```
Also, there might be DOS-style CR/LF carriage return/line feed pairs at the ends of the lines while unix expects only LFs. You can fix that problem with
the dos2unix program available in the tofrodos package.

Otherwise, inspect the data inside the pdf file some more with a text editor to see if there is something non-pdf-like in the file.

---

### Post by jmd9qs on 2008-09-05
k i tried:

```
head An_Introduction_to_Cosmology.pdf
```

and nothing came up... it waited for a second and then the prompt came back up. i piped like so:


```
 head An_Introduction_to_Cosmology.pdf | cat >> head_info_pdf.txt
```

and when i opened the file, i get an error from gedit:

> gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

---

### Post by jmd9qs on 2008-09-05
i downloaded/installed adobe reader 8, and when opening the pdf it says:

> Adobe Reader could not open 'An_Introduction_to_Cosmology.pdf' because it is either not a supported file type or because the file has been damaged (for example, it was sent as an e-mail attachment and it wasn't properly decoded)



if the pdf is "damaged", how can i tell for sure? and if it is, do i have to re-download or is there a way to fix it?

---

### Post by unutbu on 2008-09-05
I think the so-called pdf file is corrupt, or maybe it is encrypted, or compressed. I kind of suspect it is corrupt because if it were encrypted or compressed the 'file' command should have been able to recognize its true format.

---

### Post by jmd9qs on 2008-09-05
if it is corrupt, can i fix it? i literally have like 30 pdf's that are doing this... all of them are taking up from 3 to 30MB, so that's a lot of info i don't want to lose...

---

### Post by unutbu on 2008-09-05
Do you think maybe the 30 pdfs have to be concatenated to make one whopping huge pdf?

Still, the first one had better start with something like
```

%PDF-1.4
```

To concatenate files a.pdf b.pdf c.pdf:
```

cat a.pdf b.pdf c.pdf > d.pdf
```

---

### Post by jmd9qs on 2008-09-05
well, they were in one compressed folder that i downloaded... i don't know if that's what i should do though, cause they are seperate in nature (and they were in seperate folders too). i'm gonna try this dos2unix thing and see if that helps...

---

### Post by Nameless_one on 2008-09-05
The fact that they come from the same source may mean that the compressed file was corrupt during download. Maybe you should try to obtain them again.

---

### Post by jmd9qs on 2008-09-05
ya, that's what i'm thinkin.... pity, though. that took forever to download and organize. thanks for the help, though.

---

### Post by jmd9qs on 2008-09-05
i'm gonna keep this thread open for a while.... 

anybody have anything new to add, please feel free; i would still like to try and resolve this before i download again...

---

### Post by albertnet on 2008-11-22
Hi, have you ever tried to open them in a windows environment? I ask you this because I have some pdf's that somehow seem corrupt but when I open them in windows they are quite normal and readable. If you try it please let us know the result, by the way, I have my self an issue with pdf's that I haven't find nothing in the forums, it's some pdf's that don't show the fonts, I mean no text but in the nautilus preview and the evince thumbnails the text are shown. Any clues?

---

### Post by jmd9qs on 2008-11-25
sorry dude, i never got this fixed.... ended up having to re-download.

---

### Post by rodrickjaynes on 2008-12-28
yeah i'm having this problem too except i have these pdfs that work then i save them with okular under gnome and they get effed up...

what gives.

ps

noob ](*,)

---

