---
title: "Not Ubuntu - AC charging problems"
date: 2010-03-23
forum: Hardware
---

### Post by Maramros on 2010-03-23
I am trying to fix a friend's laptop, which will rapidly discharge if not plugged in. When plugged in, it will remain at 2% battery life, and will not charge or discharge. This is incredibly inconvenient, and I am not sure, after having looked around for a fair time, I am not sure what to do. If the adapter is unplugged and re-inserted, the following message appears:
"The AC power adapter type cannot be determined. Your System will operate slower and the battery will not charge. Please connect a Dell 65W AC adapter or higher for best system operation." 
The adapter is in fact a 65W adapter, it is the adapter that came with the computer, which was purchased this summer. It is a Dell Inspiron 15, running Windows Vista.
I apologize, as this is not an ubuntu-related problem, but I am unsure where to ask otherwise. Other sites answering similar problems have said it may be that the battery is dead, and that it may need to be replaced. However, I am doubtful of this, as the laptop was purchased this summer.
Any help would be appreciated. Thanks.

---

### Post by dumb_question on 2010-03-31
Hi - I logged on to try and find an answer to the exact same question. Here is what I have so far. Some useful discussion of the problem may be found here: [http://www.laptop-junction.com/toast/content/dell-ac-power-adapter-not-recognized]("http://www.laptop-junction.com/toast/content/dell-ac-power-adapter-not-recognized")

The short version is that the Dell is trying to identify the adapter, and if it can't it dials back your CPU and will not charge the battery. I am not sure if there is a legitimate reason for this, or if it is just to force you to purchase Dell branded power supplies. Anyways, if that connection is lost (one explanation is the center pin on the DC wire breaking, see above link, which is I think my problem), it can't recognize the real adapter, assumes you are using a non-Dell one, and breaks your machine.

Apparently there is software for Windows called "Notebook Hardware Control" that will let you dial your CPU back up again, although this won't solve the battery issue.

So, 3 questions for the forum denizens:

1 - is there a tool in Ubuntu or the repositories I can use to dial my CPU back up again?

and

2 - is there some linux-fu to convince the machine to ignore the whole power-supply identification thing and proceed to charge the battery anyways?


and

3 - if the answer to 2 is "no", is there a way to just charge the battery in hardware (e.g. "apply 19.5 V to pins 1 and 3 and it will charge and also you will get a pony")?

Thanks!

---

