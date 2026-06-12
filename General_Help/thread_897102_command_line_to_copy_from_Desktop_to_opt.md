---
title: "command line to copy from Desktop to /opt"
date: 2008-08-21
forum: General Help
---

### Post by Freakster on 2008-08-21
Hey guyz, 

Quick question...

i have got a zip file "filename.zip" which is located on the Desktop and i would like to extract its contents to  /opt/lampp/htdocs folder

what is the proper command line to do this?

all i know is this please help me finish is i am wrong.

"sudo -s"
"cd Desktop"
"?????? filename.zip -C /opt/lampp/htdocs" - this is the part where i am confused.

---

### Post by rockerboo on 2008-08-21
```
cp filename.zip /opt
```

If you are in the Desktop directory, that should work

---

### Post by Freakster on 2008-08-21
> **rockerboo said:**
> ```
cp filename.zip /opt
```

If you are in the Desktop directory, that should work
cp isnt that just copies the zip file to the /opt directory, not extract its internal contents..?

---

### Post by iaculallad on 2008-08-21
In your terminal:

```
cp ~/Desktop/filename.zip /opt
```

Or, if it says about security permission, try:

```
sudo cp ~/Desktop/filename.zip /opt
```

EDIT: To decompress a Zip file:

```
unzip filename.zip
```

---

### Post by x1a4 on 2008-08-21
```
sudo unzip ~/Desktop/filename.zip -d /opt/
```

---

### Post by pauper on 2008-08-21
> "?????? filename.zip -C /opt/lampp/htdocs" 

I suspect you've tried to apply "tar"'s flag -C (change to directory DIR)
to "unzip":

```
# Either:

cd TARGET
unzip SOURCE.zip

# Or:

unzip -d TARGET SOURCE.zip
```

Note: Before extracting any archive verify its contents. Make sure there is a
parent directory--who knows the intents of its author--google tar-, zip bombs.
Otherwise create one in TARGET beforehand.

```
unzip -l ~/Desktop/filename.zip
sudo mkdir /opt/new_dir
```

---

### Post by aysiu on 2008-08-21
Please don't use *sudo -s*

```
sudo -i
``` is the proper way to get a persistent root prompt.

---

