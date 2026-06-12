---
title: "Compilation of a C-program for drawing straightline segments."
date: 2008-11-14
forum: General Help
---

### Post by skmaiti on 2008-11-14
I have installed ubuntu recently. I was trying to run one C program related to graphics, just to draw straightline
segments. The program icludes the following statements at the beginning.
----------------------------
#include <stdio.h>
#include <stdlib.h>
#include <vga.h>
#include <vgal.h>
#include <math.h>
/* Program for plotting discretisation from NCAs & x,y */
/* Plotting the deformed and original shapes  */
main()
{
        FILE *TAPE1,*TAPE2;
        int  grres, grmode;
        int color = 6;
        int nca[400][10],np,ne,ndf,npe,ix[12],iy[12],n,node,i,j,k,k1,i1;
        float a,x[1200][2],x1,x2,y1,y2,xcp,ycp,xc,yc,xlft,xrght;
        float dis[1200][2],xnew[1200][2];
        int mult,multdis,nc,ntest,npdir,x3,y3,x4,y4,ntot,ntip,nrotn;
        float rad,drad,radx,rady,radsq,radlm,radlmsq,dx,dy,theta,alfa;
        vga_init();
        grmode = vga_getdefaultmode();
        if (grmode == -1) {
                grmode = G1024x768x256;
        }
        grres = vga_hasmode(grmode);
        if (grres == 0) {
                printf("\n Requested mode not avialble : %d", grmode);
                exit(1);
        }
        vga_setmode(grmode);
        gl_setcontextvga(grmode);
        gl_enableclipping();
.....
After compilation the following messages appear.

 undefined reference to vga-init
 undefined reference to vga-getdefault
 undefined reference to vga-hashmode

On checking the binaries, it was confirmed that there is no files bearing names vga.h, vgagl.h. Ubuntu downloadable area
does not either have any
files bearing such names.

Please let me know

(1) What are the files to be downloaded? From which locations/area?
(2) What is the command for compiling?

Earlier with linux the compilation statement used is as follows.

    cc <filename> -lvgagl -lvga -lm -o <outputfile>

Please help.

Thanks.

skmaiti

---

### Post by mionescu on 2008-11-18
Did you install libsvga1-dev ?

---

### Post by whitethorn on 2008-11-18
I use g++ instead of gcc to compile, gcc didn't use the libraries I had told it to ( you have to add the path to the libraries in the compile command I was too lazy for that).  g++ works well. To get the compilers you need

```
sudo apt-get install build-essentials
```

---

