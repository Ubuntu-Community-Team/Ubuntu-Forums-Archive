---
title: "Problems Installing dislin"
date: 2008-09-11
forum: General Help
---

### Post by llewellyn88 on 2008-09-11
So, i am trying to install dislin for a course i am taking and i ran into a snag when following the readme file included with the .tar.gz file. The readme says:

__________________________________________________________________________
3.) Installation of the tar.gz Distribution

a) Uncompress the tar.gz file with the command

                  gzip -d     dislin-9.3.linux.tar.gz


b) Restore files from the tar file with the command

                  tar   xvf   dislin-9.3.linux.tar    

c) Change to the extraction directory of DISLIN

                  cd    dislin-9.3

d) Choose a directory in the file structure where DISLIN should be
   installed and define the environment variable DISLIN with it:

   For example:    DISLIN=$HOME/dislin     (or: /usr/local/dislin)
                   export DISLIN
    
e) Run the install program with the command 

                   INSTALL

   This program copies files to $DISLIN and sets protections.

f) To make DISLIN available for general use, write the following com-
   mands to your .profile or to /etc/profile

                    DISLIN=directory                     
                    export DISLIN
                    PATH=${PATH}:${DISLIN}/bin

                    LD_LIBRARY_PATH=$DISLIN:$LD_LIBRARY_PATH
                    export LD_LIBRARY_PATH

   Note: The environment variable DISLIN is not necessary if DISLIN
         is installed in the default directory '/usr/local/dislin'. 

g) You can delete the directory 'dislin-9.3'.
__________________________________________________________________________

I get to step e and then run into a problem

__________________________________________________________________________
Desktop/dislin-9.3$DISLIN=/usr/local/dislin
Desktop/dislin-9.3$ export DISLIN
Desktop/dislin-9.3$ sudo ./INSTALL
[sudo] password for ____: 

     /*****************************************************************/
     /**                       I N S T A L L                         **/
     /**                                                             **/
     /** This program installs the graphics software DISLIN. The va- **/
     /** riable  DISLIN must be set to  the directory  where  DISLIN **/
     /** should be installed:                                        **/
     /** For example:  DISLIN=/usr/local/dislin                      **/
     /**               export DISLIN                                 **/
     /**                                                             **/
     /** Date   : 15.04.2008                                         **/
     /** Version: 9.3 / Linux, i586                                  **/
     /*****************************************************************/

The environment DISLIN is not defined!
__________________________________________________________________________

any ideas? thanks for the help.

---

### Post by craq on 2008-11-12
Hi,
I've now got the same problem, did you figure it out?

I also tried converting the .rpm to a .deb, which installed but ended up with the Absoft version according to the dlink output (even though I downloaded the g77 version, dislin-9.4.linux.i586.rpm, and the md5sum matched for this).

Cheers
Chris

---

### Post by meitnerium on 2008-11-28
When you configure the variable :

DISLIN=$HOME/dislin (or: /usr/local/dislin)
export DISLIN

You use your own user, not the root, but when you execute :

sudo ./INSTALL

You use the root account. The solution is to changem completely on root acces, doing :

sudo su

before starting the install, after installation, just do exit to return to user account.

---

### Post by arlexmarin on 2009-03-31
I've succeed installing DISLIN, and I went in a lot of trouble getting the g77 compiler to work in Ubuntu 8.10, but finally did it.

But when I began to feel comfortable and trying to compile a test program in f77 with the dlink option an error message appears:

$ dlink -c exa_f77
f77: /usr/local/dislin/libdisaf77.so: No existe el fichero ó directorio
f771: error: no se reconoce la opción de línea de comando "-f"

What is wrong?


Thanks, A. Marín.

---

