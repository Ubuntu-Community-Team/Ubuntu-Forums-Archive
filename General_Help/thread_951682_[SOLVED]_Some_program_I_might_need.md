---
title: "[SOLVED] Some program I might need?"
date: 2008-10-18
forum: General Help
---

### Post by Linuxidiot on 2008-10-18
So ive been having this problem with my graphics card drivers...gforce 9500 series 2.0...neway i got all excited cause i found the driver i need!!! yay...(ive been battleing this demon for a few days now)..soo i get it on the desktop and run to the terminal command to put out the command sh NVIDIA-Linux-x86-177.80-pkg1.run, but when i did i got a response of:Can't open NVIDIA-Linux-x86-177.80-pkg1.run....this demon is tougher then i thought:( any sugestions? hardy 8.04

---

### Post by Sam on 2008-10-18
You must give the file execution permissions:
```
chmod +x NVIDIA-Linux-x86-177.80-pkg1.run
```
Then run it:
```
./NVIDIA-Linux-x86-177.80-pkg1.run
```

or:

Run it like this:
```
sh ./NVIDIA-Linux-x86-177.80-pkg1.run
```

---

### Post by BUSHYBOB on 2008-10-18
You could try ENVY

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Linuxidiot on 2008-10-18
chmod +x NVIDIA-Linux-x86-177.80-pkg1.run
chmod: cannot access `NVIDIA-Linux-x86-177.80-pkg1.run': No such file or directory....now im sure this is a simple problem that im probably overlooking something

---

### Post by Linuxidiot on 2008-10-18
Envy doesnt support my card at the moment :(

---

### Post by sisco311 on 2008-10-18
> **Linuxidiot said:**
> chmod +x NVIDIA-Linux-x86-177.80-pkg1.run
chmod: cannot access `NVIDIA-Linux-x86-177.80-pkg1.run': No such file or directory....now im sure this is a simple problem that im probably overlooking something

type:
```
sudo sh 
```in the terminal and press *space* then drag and drop the file in the terminal window and press enter.

or
type:
```
sudo sh ~/Desktop/NVIDIA
```then press TAB to auto-complete.

---

### Post by Yellow Pasque on 2008-10-18
Did you change to the Desktop directory?
```
cd ~/Desktop
```
Now type 'chmod +x NV' and hit tab. bash should auto-complete the file's name

---

### Post by Linuxidiot on 2008-10-18
You all are always extremely helpfull and i appriciate it.THANK YOU!:biggrin: BTW posting the program in the terminal helped lots....One last thing, Is there some page i can visit or program i can run to give me a list of commands and what they do...theres no way i can remember all these. I get curious on exaclty what i telling the computer to do and would like to get a step further in "helping myself" with some of these noob problems im having

---

