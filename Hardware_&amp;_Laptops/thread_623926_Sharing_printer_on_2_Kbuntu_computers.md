---
title: "Sharing printer on 2 Kbuntu computers"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by rmadd on 2007-11-26
The instruction below from the Ubuntu Website, does not work. Does anyone know how to set up a shared printer on two (2) Ubuntu machines? My printer is an HP psc 1210. Need Help

Ubuntu Print Server

   1.

      On the server machine (the one the printer is attached to) open up printer manager with
          *

            sudo gnome-cups-manager 
                

            Or System->Administration->Printing.
   2.

      Under Server Settings check, i.e, turn on, the Share published connected to this system printers.
   3.

      Click on the Apply button;

Ubuntu Client Machine

Now on the client(s) (the one that you want to link to the shared printer that is in server machine):

    *

      1.Open up the printer manager System->Administration->Printing
          o

            Or open the Terminal:
                +

                  sudo gnome-cups-manager 
                      

      2.Under the Server Settings check the Show Printers shared by others systems option.

   1.

      Click on the Apply button;

Then you can open any document, and try to print it. It should appear in the printer dialogs box the name of the shared Printer.

---

