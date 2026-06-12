---
title: "How do I enable the JRE in Open Office?"
date: 2008-09-12
forum: General Help
---

### Post by rgeddes on 2008-09-12
Hi,

I have a spreadsheet in Open Office, and tried to save it as an xml file.  Open Office keeps asking for the JRE in order to complete the task.  

I'm using 64-bit ubuntu.. have sun's jre installed .. 


$>dpkg -l | grep jre
ii  sun-java6-jre                              6-06-0ubuntu1 

I've tried to point Open Office to all sorts of directories under

/usr/lib/jvm/java-6-sun/jre

and nothing is accepted and a message pops up:

"The folder you selected does not contain a jre."

Any advice is appreciated.

Regards,
Richard

---

### Post by quibbler on 2008-09-13
> **rgeddes said:**
> Hi,

I have a spreadsheet in Open Office, and tried to save it as an xml file.  Open Office keeps asking for the JRE in order to complete the task.  

I'm using 64-bit ubuntu.. have sun's jre installed .. 


$>dpkg -l | grep jre
ii  sun-java6-jre                              6-06-0ubuntu1 

I've tried to point Open Office to all sorts of directories under

/usr/lib/jvm/java-6-sun/jre

and nothing is accepted and a message pops up:

"The folder you selected does not contain a jre."

Any advice is appreciated.

Regards,
Richard
Look in:  /usr/lib/jvm/java-6-sun-1.6.0.07/jre

in your case in may be /usr/lib/jvm/java-6-sun-1.6.0.0**6**/jre

Open office...go to tools-options-java-add and it should see it.

Regards quibbler

---

### Post by rgeddes on 2008-09-15
> **quibbler said:**
> Look in:  /usr/lib/jvm/java-6-sun-1.6.0.07/jre

in your case in may be /usr/lib/jvm/java-6-sun-1.6.0.0**6**/jre

Open office...go to tools-options-java-add and it should see it.

Regards quibbler

Thanks for the response.  I tried the

tools-options-java-add

and selected the /usr/lib/jvm/java-6-sun-1.6.0.06

but I get a message 

"The folder you selected does not contain a java runtime environment.  Please select another folder."

I'm using java for other applications so I don't think java is the problem.

R

---

### Post by quibbler on 2008-09-15
In Synaptic search for jre and see what is installed.
I have sun-java6-bin  sun-java6-jre  and  sun-java6-plugin
check what you have, if it is the same try reinstalling them.
then with nautilus to to /usr/lib/jvm/java-6-sun-1.6.0.0 and 
see if you have the jre folder.

quibbler

---

### Post by jespdj on 2008-09-15
I have the same problem with OpenOffice 2.4 on 64-bit Ubuntu 8.04. I have both OpenJDK Java 6 and Sun Java 6 installed, and OpenOffice recognises neither of them.

I think this is a bug, so I reported it in the bug database: [270476](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/270467)

---

### Post by Icebear on 2008-09-15
Hi

I believe you need the OpenOffice.org-java-common pakage. Searh for it Synaptic Package Manager. This what work for me with a 32 bit machine.

---

### Post by rgeddes on 2008-09-15
> **Icebear said:**
> Hi

I believe you need the OpenOffice.org-java-common pakage. Searh for it Synaptic Package Manager. This what work for me with a 32 bit machine.

Yes!  I installed this package and I did not even have to search for the directory of the jre... as soon as I selected the Java option it displayed it in it's select list.

Thank you!

---

