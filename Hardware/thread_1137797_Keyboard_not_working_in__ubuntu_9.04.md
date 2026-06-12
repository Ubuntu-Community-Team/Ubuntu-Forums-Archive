---
title: "Keyboard not working in  ubuntu 9.04"
date: 2009-04-25
forum: Hardware
---

### Post by Aakash on 2009-04-25
Please be informed that I'm a real newbie for Linux. But I'm somehow attracted to Linux for it's simplicity and usability.

Recently I downloaded and installed Ubuntu 9.04 in my 2 gb pen drive (using windows interface) and booted it for live experience. Everything went fine...., but the keyboard....

I'am using Lenovo y 500 series laptop and while I booted from pen drive I am unable to type anything, as it is not detected by Ubuntu. All the other features are working fine.

(P.S. all the hardware's are working fine with Win xp)

Hoping to get a clue

Thanking all in advance

Aakash

---

### Post by KhurramM on 2009-04-26
Was the LiveCD working with your keyboard. Obviously yes u installed it.

But u had to select the correct keyboard. I think u have made an error here.

Which features are working fine, if u cant login with out a keyboard??????????????????

---

### Post by Aakash on 2009-04-27
KhurramM

Thanks for your response!

Concerning to the features that are working fine;

I mean I can boot, I can surf, I can play multimedia files and view (not edit) existing files in my machine, with the help of the mouse.:)

Though I am very new to Linux, I did tried to alter the keyboard settings, but couldn't figure it out.

 Any clue??

---

### Post by Didius Falco on 2009-04-28
Hi Aakash,

I found this while doing a search, so I have no clue if it will work for you or not. It did work for several other, and they are all using Lenovo 3000 Y500 laptops, though.

Please post back the results, so I'll know if it works, in case the question comes up again.

You need to edit your menu.lst file. You can do this from within Ubuntu using a Terminal shell. The first thing to do is backup the menu.lst file, so you have a copy to restore if needed. In the Terminal window, type ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```Then type ```
gksudo gedit  /boot/grub/menu.lst 
```In the menu.lst file, you'll see a list of kernels, something like this:

```
title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid           e02ddaef-9065-4851-a66f-b417af080bc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```You want to add "i8042.reset" to the end of the kernel line, so the above would like like this:

```
title            Ubuntu 9.04, kernel 2.6.28-11-generic
uuid           e02ddaef-9065-4851-a66f-b417af080bc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro quiet splash i8042.reset
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```Try with just the top entry, the one you normally boot into. Save the file and reboot. Try it out for a while, reboot a few times and see if it makes a difference.

If it fixes it, remember to go back into the menu.lst file and add it to the end of all the other "kernel" lines.

Also, remember to edit your menu.lst every time you get a kernel update and add it to the new kernel lines.

I hope this fixes the problem - please post back and let us know

---

### Post by Aakash on 2009-04-28
Helllo!
Didius Falco !!

Thank you very much for your time and detailed response. 

Once again let me make one thing very clear that I am a real newbie for Linux.

In your response, you have asked me to edit menu.1st file, which requires 'typing' and as my keyboard is  not working I'am unable to do so.

Next what I tried was I copied all the command lines you have mentioned, in a pen drive (thinking that I'll do 'copy' 'paste' in Terminal window. But after pasting the lines in terminal window I found that I can not hit even the "Enter" key, so it didn't worked.

Now what I am thinking is:

is it possible to somehow copy the menu.1st file into pen drive and edit it using win xp? 

If possible, I'll edit it and then replace the old menu.1st file with new one.

If it is possible, please advice me where is the file "menu.1st" located, so that I can find it and copy into my pen drive for edit ( As I am very new for Linux I couldn't find the file also)

Thanks again !

Aakash

---

### Post by Didius Falco on 2009-04-28
Aakash,

Can you try it with the Live CD you used to install it? 

Just boot with that, choose the "make no changes to my PC" option and then edit the menu.lst file from there.

The file is located at  /boot/grub/menu.lst. Note that it is an L, not the number 1 in the filename, and remember that linux is case sensitive. If you try to open "menu.Lst" it's going to tell you it doesn't exist. 

the command below will open it in Editor from the Live CD, when typed into a terminal.

```
gksudo gedit  /boot/grub/menu.lst
```

---

### Post by Aakash on 2009-04-28
Helllo!
Didius Falco !!

I Think I should have explained it before, I installed ubuntu 9.04 into my pen drive using the iso file directly with the help of windows based software called: 
"UNetbootin" ( [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/))

So I'm not having a live cd too ( I just have live pendrive).

Also I tried to search the "menu.lst" from Places>>Search for files.. but the file was also not found.

Now I am assuming that it was not properly installed in my pen drive and planning to install it again.

I'll be back if I can make it work.

Thanks !

---

### Post by Didius Falco on 2009-04-29
If you can do so, download the ISO and burn a cd...it can be very useful. Lacking that, go to the Ubuntu website and they'll mail you one for free. Probably better to wait a few days, though - they are probably swamped with requests right now, with 9.04 just coming out.

---

### Post by Aakash on 2009-04-29
Didius Falco
Thanks again 

I'll also search for solution and also write to Lenovo for any hardware related fix/clue.

I'll come back once the problem is solved.

Aakash

---

### Post by gorski on 2009-04-29
Hi!

I am running Ubuntu 9.04 on a 64b machine [Acer 5920G lappy] and can't get an additional language installed. I mean, I did - but it doesn't work.

First, the Acer laptop keyboard is not installed correctly, even though it's there, as an option. Then the Croat characters do not work, either, I'm afraid... The same UK default I installed at the installation...

When one tries/chooses and then types in the same window to test - nothing happens with the Slavic characters...

Any help possible, please?

---

### Post by bdebasish on 2009-05-27
Didius Falco!

Thx, your solution worked for me. I am using a Dell Vostro 1510 and the keyboard, touchpad was not working after a reboot. After your fix they seem to work..thx. What was the problem BTW?

---

### Post by kumarnum1 on 2009-05-29
Hi Didius,

I followed your instructions but that didn't solve the problem. Any other suggestions?

Thanks,
Kumar

> **Didius Falco said:**
> Hi Aakash,

I found this while doing a search, so I have no clue if it will work for you or not. It did work for several other, and they are all using Lenovo 3000 Y500 laptops, though.

Please post back the results, so I'll know if it works, in case the question comes up again.

You need to edit your menu.lst file. You can do this from within Ubuntu using a Terminal shell. The first thing to do is backup the menu.lst file, so you have a copy to restore if needed. In the Terminal window, type ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```Then type ```
gksudo gedit  /boot/grub/menu.lst 
```In the menu.lst file, you'll see a list of kernels, something like this:

```
title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid           e02ddaef-9065-4851-a66f-b417af080bc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```You want to add "i8042.reset" to the end of the kernel line, so the above would like like this:

```
title            Ubuntu 9.04, kernel 2.6.28-11-generic
uuid           e02ddaef-9065-4851-a66f-b417af080bc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro quiet splash i8042.reset
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```Try with just the top entry, the one you normally boot into. Save the file and reboot. Try it out for a while, reboot a few times and see if it makes a difference.

If it fixes it, remember to go back into the menu.lst file and add it to the end of all the other "kernel" lines.

Also, remember to edit your menu.lst every time you get a kernel update and add it to the new kernel lines.

I hope this fixes the problem - please post back and let us know

---

### Post by gorski on 2009-06-05
So, I take it no South-Slavic users here? :(

---

