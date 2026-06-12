---
title: "RS232 thrue USB, Ubuntu 9.10, VirtualBox to Windows XP"
date: 2009-12-09
forum: Hardware
---

### Post by AntonJ on 2009-12-09
I have had a problem with configuring Virtual Box to let XP use RS232, which is connected by USB to RS232 convertor.
I used command:
**dmesg | grep tty**
[B][ 7682.216606] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[ 7687.597459] usb 6-2: pl2303 converter now attached to ttyUSB0[/B]
Next thing I used to do is configure VirtualBox Serial ports (at the Port1 tab: check Enable Serial Port, in Port Number:COM1; )
[IMG]https://files.one.ubuntu.com/12aa265e-e797-4b93-b002-03318da442d3[/IMG]

Next thing is XP I did installed communication port COM1 
1) use "Add hardware", in control panel.
2) after wizard is finished searching, and ask "Is the hardware connected?" check "Yes, ...bla bla bla" and press Next
Actually I do not remember the end of XP process, but that was easy, just press Ok, Next, Yes, Other device and so on.
after restart all should work properly.
I have tested HyperTerminal and two factory devices all communicate properly
Good luck.

---

### Post by youbuntu on 2009-12-11
"Blah blah blah" is not technical enough an explanation... would you mind making your tutorial clearer?. I need this function, thanks.

---

