---
title: "OOo3 Inserting Movies and Sound--Not Working?"
date: 2008-11-03
forum: General Help
---

### Post by seuzy13 on 2008-11-03
Every file format that I try to insert into OpenOffice 3's Impress gives me this message: "The format of the selected file is not supported."

I have tried avi, mp3, wav, mov, mpg4, and even wmv. All give me the same message.

Is there any preferably simple way I can resolve this? Also, I just upgraded to Intrepid, if that matters.

Thanks!

---

### Post by RevNomad on 2009-01-15
::Bump::

I just tried inserting a mov file into Impress. It tells me this file is not supported. 

How do I correct this?
NTP

---

### Post by cariboo on 2009-01-15
I just inserted an mp4 file in Impress, and it works as it should. Have you installed ubuntu-restricted-extras? It is available in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by RevNomad on 2009-01-17
Yes, the restricted extras are installed. I'm strictly amateur but I'm concerned the Java Media Framework is not installed or not installed properly. I have no idea how to check this or install it. Instructions would be helpful. The instructions I have found assume I know more than I do.:confused:

NTP

---

### Post by zolek78 on 2009-03-26
I'm encountering the same problems and i found this

go to 
[http://java.sun.com/products/java-media/jmf/2.1.1/download.html](http://java.sun.com/products/java-media/jmf/2.1.1/download.html) and download 
jmf-2_1_1e-linux-i586.bin. Then install it according to the following 
directions using the command line. For this, I am assuming you have OOo 
installed in /opt/. You will also have to become root to do this. 
1) Move JMF to the /opt/ directory. 
2)   chmod o+x (Make sure JMF is and executable file.) 
3) ./jmf-2_1_1e-linux-i586.bin (This installs it.) 
4)  export 
CLASSPATH=$JMFHOME/lib/jmf.jar::$JMFHOME/lib/sound.jar:.:${CLASSPATH} (Make 
sure this is on only one line.) 
5)export LD_LIBRARY_PATH=$JMFHOME/lib:${LD_LIBRARY_PATH} 
6) Open OOo. 
7) Tools > Options > OpenOffice.org > Java. 
    a) Click the "Class Path" button. Then click "Add Archive". 
    b) Browse to /opt/JMF-2.1.1e/lib/. 
    c) Click jmf.jar. 
    d) Click OK. 

(it belongs to a guy name Dan-Lewis on Nabble)

I'm gonna give it a try to see what will happen

---

