---
title: "PC Won't Power Off at Shutdown"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by oldnoob on 2006-11-26
I installed Xubuntu a few days ago with no problems.  But when I shutdown, my PC won't power off by itself - I have to physically hit the power button.  Xubuntu shuts down fine until all that is left is the Xubuntu splash screen.  Then I hit the button.

I looked through the posts and I see I should include apci=force in  /boot/grub/menu.lst.  However, I have a very old PC (BIOS circa 1999) and in my dmseg file I get the message "ACPI: Unable to locate RSDP".  Other posts indicate that I should use acpi=off to clear this message.

So what's the answer?  The RSDP message does not seem to be causing any problems.  I would really like to have the PC power itself off.  Would I be OK going along with adding acpi=force to my /boot/grub/menu.lst?

---

### Post by drphilngood on 2006-11-27
Does [this]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961") sound familiar?;)

---

### Post by oldnoob on 2006-11-27
drphilngood - thanks for the reply.  I did look through that bug doc and my issue is very similar.  I don't get the "Will not halt" message that some others are getting, but that may be due to the fact I'm using Xubuntu directly.

Looking through other posts on the forums it appeared the acpi=force boot option was helping some and I wondered if it was a workaround.  But I hesitated trying that since as I mentioned, I am also getting the "Unable to locate RSDP" message.  Using acpi=force for the shutdown issue seemed to contradict the suggestion for the RSDP message which is acpi=off.  

So I was looking for a little more direction.  Thanks.

---

### Post by Kross on 2006-11-29
This Worked For me,,,

[http://www.ubuntuforums.org/showthre...light=shutdown](http://www.ubuntuforums.org/showthre...light=shutdown)

4th Post down...
Post there If it worked for you..

Thanks

-Kross

---

### Post by drphilngood on 2006-11-30
> **Kross said:**
> This Worked For me,,,

[http://www.ubuntuforums.org/showthre...light=shutdown](http://www.ubuntuforums.org/showthre...light=shutdown)

4th Post down...
Post there If it worked for you..

Thanks

-Kross

Can you repost the link?

---

### Post by Kross on 2006-12-07
> **drphilngood said:**
> Can you repost the link?

I'm Sorry I can't find that link..SO I will just repost here...

[COLOR="Red"]I upgraded an (old) system from sarge to etch, which was impressive, almost 
everything worked out of the box as in sarge (only better due to new 
software:-)

The only flaw I saw is that after running "shutdown -h now" power is not shut 
down any more.

Since the system is old, it uses apm and after googleing for the problem, I 
added

append="acpi=off apm=power_off"

to /etc/lilo.conf and 

[COLOR="Green"]apm power_off=1

in /etc/modules
[/COLOR]
Now, this powers off the system again at the end of shutdown.

Not sure if there is an easy way to avoid that others have to search for this 
information as well. Little effort would be to add this to the release 
notes... and a big benefit for the guys with old hardware who read release 
notes ;-)[/COLOR]

Now I use grub so acpi=off apm=power_off in my /boot/menu.lst file.

AS such =
## ## End Default Options ##
[COLOR="Red"]
title		Debian GNU/Linux, kernel 2.6.18-3-k7
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.18-3-k7 root=/dev/hda2 ro [COLOR="Green"]acpi=off apm=power_off[/COLOR]
initrd		/boot/initrd.img-2.6.18-3-k7[/COLOR]

From what I can understamd this is a command problem within the new
 kernels dealing with Power Management. eg..ACPI.,and believe this 
force it to use APM.

Now It is Also For me to say that there were a few poeple whom this
 did not work..There was a restore in this case someone had this
 problem posted,,But I no longer have the link.

If anyone has this Not work..and Knows this restore please post.

Rereading the post this may not be what you are asking..
But The apm power_off=1 is what did it for my system.

Thanks, And good luck.

<=Kross=>

---

### Post by djtecha on 2007-02-11
I am running the 6.10 version and do not have this file for some reason, looked in both root and normal user and also used show hidden folders? is there any logical reason why I cannot find this folder?

---

### Post by graabein on 2007-02-17
> **oldnoob said:**
> drphilngood - thanks for the reply.  I did look through that bug doc and my issue is very similar.  I don't get the "Will not halt" message that some others are getting, but that may be due to the fact I'm using Xubuntu directly.

Looking through other posts on the forums it appeared the acpi=force boot option was helping some and I wondered if it was a workaround.  But I hesitated trying that since as I mentioned, I am also getting the "Unable to locate RSDP" message.  Using acpi=force for the shutdown issue seemed to contradict the suggestion for the RSDP message which is acpi=off.  

So I was looking for a little more direction.  Thanks.

Did you get anywhere with this? I have the same problem. The *RSDP message* disappeared when I added **acpi=off** but it will still not power off automatically with **apm=power_off** after shutdown.

---

### Post by spd106 on 2007-02-28
After adding these lines to my feisty install it does power off, but it does it very violently. It's no better than pressing the power button. Edgy is just as bad and seems far less stable. I get random reboots, at least I think this was what caused it. On Dapper it is far more stable and has a gentle shutdown.

---

### Post by sylvaticus on 2007-03-01
On my toshiba Satellite 4060 XCDT the only way it worked was with acpi=force .
Thank you ;-)

---

### Post by rocktorrentz on 2007-12-18
I'm running arch linux on a Biostar M6TZA board using the Intel 440ZX chipset. Thought I'd let everyone know that adding "acpi=off apm=power_off" to the kernel line in menu.lst worked :D

---

