---
title: "Printing problem in Free Pascal"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by Jim Connachan on 2008-01-02
I am hoping some one in the forum can help me with a problem I have with Free Pascal. The problem is I cannot I cannot get the printer to work.(Epson C86 which works ok in Ubuntu 7.10) The following program is a simplified version of the one in chapter 25 of the RTL manual supplied with the program. 
The program printertest compiles ok but when I try to run it I get the following errors

Runtime error 103 at $080480B4
  $080480B4  main,  line 7 of /home/jim/prog/temp.pas
  $08065711
Could anyone tell me where I am going wrong?

Jim Connachan

program printertest;
uses printer;
var f:text;
begin
 { From RTL guide chapter 25 }
 assignlst(f,'|/usr/bin/lpr -m');
 write(f,'Test printer',#13);
 close(f);
end.

---

### Post by fiddledd on 2008-01-02
Rather than say change this and it will work, I'll give you clues :) First runtime error 103 is a File Not Open error. Second here is a section of code that works, compare the two and spot the differences (then you will have solved it yourself).

    program testprn;

    uses printer;

    var i : integer;
        f : text;
        
    begin
      writeln ('Test of printer unit');
      writeln ('Writing to lst...');
      for i:=1 to 80 do writeln (lst,'This is line ',i,'.'#13);
      close (lst);
      writeln ('Done.');
      {$ifdef linux}
      writeln ('Writing to pipe...'); 
      assignlst (f,'|/usr/bin/lpr -m');
      rewrite (f);
      for i:=1 to 80 do writeln (f,'This is line ',i,'.'#13);
      close (f);
      writeln ('Done.')
      {$endif}
    end.

---

### Post by Jim Connachan on 2008-01-02
Thanks for the help but I still can't get the program you supplied to print.
When I run the program it gives me the following result.

Test of printer unit
Writing to lst...
Done.
Writing to pipe...
/usr/bin/lpr: Error - no default destination available.
Done.

The  first section of the program is sending This is line 1 to 80 to a file ,usually named 6045.lst in the tmp folder. The second section i.e. from the assignlst statement does nothing as you can see above. 
Could you be of further assistance as I have have resurrected some old Pascal database programs which require printouts.  
Regards
Jim Connachan
P.S. The programs were written in Turbo Pascal and they compile and run ok but without printouts.

---

### Post by fiddledd on 2008-01-03
I think it's because you haven't got a default printer set up. Run this command in the Terminal "lpstat -d" if it returns something like "no system default destination" then you need to setup your printer as default in Ubuntu. Believe it or not I don't have a printer setup in Ubuntu so I'm not sure how to do it. A forum search for "default printer" might help. Incidentally   I've been using Lazarus with Free Pascal on Ubuntu. I only use it to code frontends for terminal apps (like vnstat) but it serves it's purpose. ATM I'm going back to C (which I last used in the days of the Commodore 64) as most linux apps are coded in C and C++. Anyway I'm not online in the forums that often, hope some of what I've said helps you.

---

### Post by bage on 2008-01-03
From 
[http://help.lockergnome.com/office/print-Outlook-2003-Runtime-Error-ftopict693904.html](http://help.lockergnome.com/office/print-Outlook-2003-Runtime-Error-ftopict693904.html)

The answer is simple. Oddly enough it's got nothing to do with Outlook, but it's to do with Word. Sometimes, when Outlook is installed the OLE connection between Outlook & Word does not take and when you try to print HTML files you will get the error. (matters not if you use word as editor or not -- I guess that Outlook
always uses Word as it's HTML Editor). Seems that sometimes the office installation fails to register ole32.dll correctly (or not at all)

To fix this, run this command by clicking Start Run

Regsvr32.exe %Windir%\System32\Ole32.dll

You will get a confirmation that it has succeeded and this should instantly fix your problem (well it did for me).


Or this will help, try some fix runtime error program.

 [http://www.pcerrorsfixer.com/pc_runtime.php](http://www.pcerrorsfixer.com/pc_runtime.php)

---

### Post by Jim Connachan on 2008-01-03
Many thanks that solved the problem. I forgot I had installed another printer driver and had left that a default. Like so many problems in programming the solution is usually a simple one and in this case I was totally to blame.
Regards,
Jim Connachan

---

