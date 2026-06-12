---
title: "Stop Update Manager from offering update"
date: 2008-07-10
forum: General Help
---

### Post by wyhog on 2008-07-10
Ubuntu 8.04

I have removed sun-java6 and I use sun-java5-bin (-plugin and -jre) because I could not get many sites to work with sun-java6 nor with open java. Those sites work fine with sun java 5. 

What I want to know is if there is any way to stop Update Manager from wanting to update my java 5 to java 6 all the time. As it is now, I have to manually uncheck the three sun-java6- items every time update manager runs. Is there a way to tell Update Manager "Don't show these again"?

I have tried using Synaptic to highlight the three sun-java6- items and then check the "Lock version" checkbox under Synaptic's menu/Packages but it doesn't seem to stop Update Manager from continually offering to update java5 to java6.

(edit)
In fact, I just ran Update Manager and I unchecked the sun-java6-bin, sun-java6-jre, and sun-java6-plugin items then clicked on the Install Updates button. It started to DL the updates and the first one it attempts are the _unchecked_ sun-java6 ones!! I have to hit Cancel because I do NOT want my java5 updated to java6 and I do not want java6 installed. How can I stop this?

Wyhog

---

### Post by iaculallad on 2008-07-10
Navigate to System->Administration->Synaptics Package Manager. Search for the java5 package and click on it to be highlighted. Click on the "Package" menu on Synaptics and select "Lock Version".

---

### Post by wyhog on 2008-07-10
> Navigate to System->Administration->Synaptics Package Manager. Search for the java5 package and click on it to be highlighted. Click on the "Package" menu on Synaptics and select "Lock Version".

See the 3rd paragraph of my original post. I did that. It makes no difference to Update Manager as Update Manager still wants to DL (and install?) the sun-java6 packages which I have UNchecked in Update Manager and which I do not want installed.

> I have tried using Synaptic to highlight the three sun-java6- items and then check the "Lock version" checkbox under Synaptic's menu/Packages but it doesn't seem to stop Update Manager from continually offering to update java5 to java6

Whoops! Sorry. I see that I typed that wrong. I typed that I locked sun-java6 but what I really did was lock sun-java5. And it makes no difference, Update Manager still wants to DL and install the sun-java6 packages.

Wyhog

---

### Post by iaculallad on 2008-07-10
My bad: Being too hasty.

Had you tried to lock the application version using the **hold** option for aptitude?

```
sudo aptitude hold package_name_for_java5
```

NOTE: This could be similar to Synaptic's version lock feature.

---

### Post by dcstar on 2008-07-11
> **wyhog said:**
> Ubuntu 8.04

I have removed sun-java6 and I use sun-java5-bin (-plugin and -jre) because I could not get many sites to work with sun-java6 nor with open java. Those sites work fine with sun java 5. 
.........
I have tried using Synaptic to highlight the three sun-java6- items and then check the "Lock version" checkbox under Synaptic's menu/Packages but it doesn't seem to stop Update Manager from continually offering to update java5 to java6.
.........

AFAIK the Update Manager will not prompt you to update releases, only versions of what you already have installed.

If you are being prompted to update java6 items then that is because you either have these installed, or have a Java meta-package installed, or there is something else that has these as dependencies.

You have to find what you do have installed and lock those versions.

---

### Post by wyhog on 2008-07-11
Well it baffles me. I used Synaptic and had it display all installed packages and then I eyeballed thru the list and I found nothing with Java in its name except the java5 stuff I have installed and version locked, and java-common. 

I then used Synaptic to search for "java" in any package's name or description. I then eyeballed thru that list and I didn't see anything that popped right out at me. 

So I guess I will have to live with it.

However, I still would like to know why when I UNcheck the java6 update packages offered in Update Manager it goes right ahead and DL's and installs java6 anyway. What good are those checkboxes next to each updatable package if Update Manager ignores whether they are checked or unchecked? They were all 3 unchecked yet update manager went ahead and installed java6 and after it was done with all updates I had to use Synaptic to remove the java6 stuff again.

Wyhog

---

