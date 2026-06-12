---
title: "Legal or illegal?"
date: 2008-08-29
forum: General Help
---

### Post by kortez on 2008-08-29
This may, or may not, be a question with an obvious answer but, is is legal to run a copy of Windows XP that is installed on another computer in Virtual Box in Ubuntu?

---

### Post by Oldsoldier2003 on 2008-08-29
That would be a license violation unless you have licenses for more than one seat.

---

### Post by ashmew2 on 2008-08-29
never mind...

---

### Post by jigsaws on 2008-08-29
I'm not sure, but if it is only copy (no installed on another computer or virtual) then yes. But only with XP, not Vista (Home, I don't know what about Ulitimate or Bussines).

---

### Post by milasch on 2008-08-29
This depends on the type of Windows license you have. If you are talking about an OEM license, then it's a violation to install in any other computer than the one the license is originally meant to. Now, if you bought a retail I'm not 100% sure that you can install on every computer you want, making sure to uninstall on the previous one (in order to not violate the number of licenses). But I know if you activate an OEM license, it sort of registers your hardware configuration, and you can't activate it anywhere else.

Now I believe if you activate a windows license in virtual box, you'll pretty much be tied up with the hardware virtual box emulates (although Memory/Hard Drive have some flexibility).

---

### Post by jvincent08 on 2008-08-29
If you have an OEM license (the computer came with Windows XP pre-installed by the manufacturer), you cannot install it on any other machine, whether you uninstall it first or not.

If you have a Retail license (you bought Windows XP at a store and installed it yourself), you may install it on as many computers as you want as long as you remove it from the old machine first (so it can only be installed on one computer at a time). I'm not exactly sure how to deactivate and uninstall Windows and its license properly so that you are able to do this, but google should help.

If you have a Volume License (you are a business and Windows was sold to you under a direct purchase agreement with Microsoft) you may install the software on multiple computers at one time, using the same license key.

[Source.]("http://en.wikipedia.org/wiki/Windows_XP#License_and_media_types")


Disclaimer: The above information is relevant to Windows XP Home, Professional, and Media Center Edition, and may or may not apply to other versions of Windows as well.

---

### Post by mb_webguy on 2008-08-29
Isn't Windows *fun*!?

:rolleyes:

---

### Post by jerome1232 on 2008-08-29
One point I've been confused on, Retail license, Dual boot Ubuntu/Win, on Ubuntu you have a vm with the same copy of windows in it, technically it's on one computer...

---

### Post by mb_webguy on 2008-08-29
> **jerome1232 said:**
> One point I've been confused on, Retail license, Dual boot Ubuntu/Win, on Ubuntu you have a vm with the same copy of windows in it, technically it's on one computer...

It *should* be legal, since the OS is only installed on a single machine.  However, you may have problems activating it since Microsoft is going to see two different installations with two different sets of specs.  I don't think it's technically against the EULA, but Microsoft won't like it.

Of course, they don't like anything dealing with any OS or software they don't produce, so that's nothing new...

---

### Post by jvincent08 on 2008-08-29
> **jerome1232 said:**
> One point I've been confused on, Retail license, Dual boot Ubuntu/Win, on Ubuntu you have a vm with the same copy of windows in it, technically it's on one computer...

That's why the EULA counts in numbers of activations, not number of machines. If you install it twice on the same computer, it's still against the EULA if you don't deactivate the original install first because you would have activated it twice.

But if Windows is already installed and you're dual booting Linux, can't you simply boot into the installation with the VM, avoiding multiple activations? I've never done it so I'm not sure, but that's the way I understood it to be.

---

### Post by aysiu on 2008-08-29
You have to read your EULA carefully to figure it out.

After all, many companies and schools have site licenses that allow them to install the same version of Windows on multiple computers.

Chances are, if you're a home user, it's not legal (if the laws of your country respect licensing agreements) to have it installed in a virtual machine *and* another computer at the same time.

---

### Post by jerome1232 on 2008-08-29
It works that's how I have it setup, I have to call them to activate the second copy inside the vm.

I do that because of work related websites that refused to work on anything other than IE in a windows environment, VirtualBox with seamless integration is much better than a reboot for a site.

I keep the real install because I do enjoy the occasional game and don't like fighting with wine.

edit: spelling corrections

---

### Post by jimv on 2008-08-29
The legality is of little consequence if you're doing this in your own home.  There are no License Agreement police that will come take you away.

The two problems that you may encounter are that you probably won't be able to actually install with an OEM CD, as they only install on the brand of computer they were meant to...at least that has been my experience with Dell XP cds.

The other problem is that you probably won't be able to activate XP, which isn't too big of a deal, but you won't be able to get updates.

---

### Post by jvincent08 on 2008-08-29
> **jimv said:**
> The legality is of little consequence if you're doing this in your own home.  There are no License Agreement police that will come take you away.

The two problems that you may encounter are that you probably won't be able to actually install with an OEM CD, as they only install on the brand of computer they were meant to...at least that has been my experience with Dell XP cds.

The other problem is that you probably won't be able to activate XP, which isn't too big of a deal, but you won't be able to get updates.

Well, sure, if you want to do things the illegal way, you can always download and apply a small patch to avoid activation all-together, AND you get access to updates ;)

---

