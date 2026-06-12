---
title: "java in netbook remix"
date: 2010-09-08
forum: Hardware
---

### Post by netopalis45 on 2010-09-08
I am taking a Java programming class this semester and instead of carrying a full-sized laptop around with me I carry an Asus EEEPC with Ubuntu Netbook Remix 10.04 and connect to the school server using ssh. When I try to compile and run a program that we wrote in class (that has a gui) I get an error that says:
Exception in thread "main" java.awt.HeadlessException: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
        at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:159)
        at java.awt.Window.<init>(Window.java:432)
        at java.awt.Frame.<init>(Frame.java:403)
        at javax.swing.JFrame.<init>(JFrame.java:202)
        at TicTacToeV4.<init>(TicTacToeV4.java:14)
        at TicTacToeV4.main(TicTacToeV4.java:299)

What do I need to do to make this stop happening and run the program properly?

---

### Post by netopalis45 on 2010-09-08
UPDATE: does not work with ubuntu desktop edition either. but if i have the file locally it does work. could this be a problem with ssh?

---

