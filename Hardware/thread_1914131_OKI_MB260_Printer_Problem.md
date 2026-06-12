---
title: "OKI MB260 Printer Problem"
date: 2012-01-23
forum: Hardware
---

### Post by yugotek on 2012-01-23
**OKI MB260 Printer Problem**             
                                                               
 I have an all  in one printer, MB260, which runs through Windows/samba-network printer.  I found an OKI driver for Ubuntu, followed the directions and installed  it for both printing and scanning. When I select a page to print or a  test page, the printer wakes up from power-save mode, but it doesn't  print. The driver is similar to the one I used with Mac OSX - Laser  ProLL2PCL. The little screen on the printer shows the 'Printing PC' for  about a second, so there is a connection.

 Anyone know what the problem is? Thank you.

---

### Post by bluexrider on 2012-01-24
Make sure the Print Server is connected and the winbind daemon is started. 

Find this under Boot-up Manager.

---

### Post by yugotek on 2012-01-26
> **bluexrider said:**
> Make sure the Print Server is connected and the winbind daemon is started. 

Find this under Boot-up Manager.

I have trouble setting up winbind - that said, I connected the printer directly to my ubuntubook and it still doesn't print.

---

### Post by bluexrider on 2012-01-26
Ok, so you connected the printer directly to the netbook. Did it ask for a configuration of sort?

---

### Post by yugotek on 2012-01-27
> **bluexrider said:**
> Ok, so you connected the printer directly to the netbook. Did it ask for a configuration of sort?


I got it working;)

The driver package I downloaded included several drivers- I had picked the wrong one. So I started to 
go through each one until it started working. There was no need to edit any file, or install anything else.

So if anyone else has Oki MB260, you need the MB200 linux drivers. Once installed, do not pick the recommended one, choose the one underneath and it will work.

---

### Post by bluexrider on 2012-01-27
Glad you got it going. Please mark this
(SOLVED)

---

### Post by rmarduk on 2012-03-28
I have the smae probolem with this printer but I don't understand what is written here:

"So if anyone else has Oki MB260, you need the MB200 linux drivers. Once  installed, do not pick the recommended one, choose the one underneath  and it will work."

 "Once  installed" so I understand that I have to instal the drivers. But what is this:

"do not pick the recommended one, choose the one underneath" where do you have this ?

---

### Post by rmarduk on 2012-03-28
I solved it.


THIS IS HOW YOU GET YOUR OKI MB 260 TO WORK.

FIRST DOWNLOAD THE DRIVERS FROM THE INTERNET, OKI WEB SITE. MINE WERE MB200_Linux.tar_tcm3-120732.gz. NOW UZIP THEM AND GO TO THE FOLDERS THERE AND UNZIP THE ARCHIVE FILES THAT ARE THERE. I UNZIPED THEM INTO THREE DIFFRENT FOLDERS.  THERE ARE TWO FOLDERS IN THE PRINTER FOLDER AND ONE SCANNER FOLDER.  AFTER THIS YOU WILL HAVE 3 SETUP FILES, TWO FOR PRINTER AND ONE FOR SCANNER. INTALL ALL OF THEM. NOW GO TO [http://localhost:631/](http://localhost:631/) CONNECT YOUR PRINTER TO THE COMPUTER AND GO TO ADD PRINTER ON THE localhost PAGE. ADD THE PRINTER AND CHOOSE THE OKI PRINTER THAT IS CONNECTED. THEN FROM THE LIST OF PRINTERS (DRIVERS) LOOK FOR:

Laser Pro LL2 PCl

YOU SHOULD FIND TWO SUCH THINGS NOW CHOOSE ONE OF THEM AND COMPLETE ADDING THE PRINTER. AFTER THIS TRY TO PRINT A PAGE. DOES IT WORK ? NO ? THEN GO BACK TO THE PRINTER AND EDIT IT NOW CHOOSE THE OTHER Laser Pro LL2 PCl THAT YOU HAVENT CHOOSEN AND SAVE. NOW TRY TO PRINT. AFTER THIS IT SHOULD WORK. TRY TO PRINT A TEST PAGE.

SO WHAT IS THE BASIC PROBLEM:

CHOOSE THE RIGHT DRIVER FROM THE TWO THAT YOU HAD INSTALLED AND TRY TO PRINT ON ONE OF THEM. ONE OF THEM IS THE RIGHT ONE.

I HOPE I COULD HELP. BECAUSE I WASTED A LOT OF TIME ON THAT.

---

### Post by mörgæs on 2012-03-28
Moved to the hardware forum.

---

