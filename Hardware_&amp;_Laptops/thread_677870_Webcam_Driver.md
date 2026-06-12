---
title: "Webcam Driver"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by cesar_spain on 2008-01-25
Dear all:

     I have written a small script for installing webcam driver. You need kernel header in order to compile the code.

 > 
#!/bin/bash

#####################################
# INSTALL_CAM
#####################################
#  Script for installing the webcam
# on a PC
#####################################
# Version: 1.0
# Date   : 10-March-2007
#####################################

##################################
# ENVIRONMENT
#################################

# 0.- General Variables
#----------------------
ERROR=1
OK=0


# 1.- Where to download
#----------------------
WORK_DIR=$HOME
OLDER=(spca5xx-20060501.tar.gz \
       [http://mxhaard.free.fr/spca50x/Download/](http://mxhaard.free.fr/spca50x/Download/)   \
       )

NEW=(gspcav1-20071224.tar.gz \
     [http://mxhaard.free.fr/spca50x/Download/](http://mxhaard.free.fr/spca50x/Download/)   \
     )

################################################################################
# MODULE MISCELLANEOUS ====> GENERAL FUNCTIONS 
################################################################################

#-----------------------------------------------------------------------
# AYUDA 
#-----------------------------------------------------------------------
#  Muestra la ayuda por pantalla
#-----------------------------------------------------------------------

ayuda()
{
   echo "Mostrando ayuda" | more
}


#-----------------------------------------------------------------------
# TRATA_ERRORES
#-----------------------------------------------------------------------
#   Trata todos los posibles errores del script.
#
#    Se considerar salida err ea a toda salida del script sin la creaci 
#  de una estructura de datos (por ejm.: opcion -h provoca salida errea).
#
#     Variables de entrada:
#         $1 = Tipo de Error
#         $2 = Ruta a la que el usuario no tiene acceso (inexistencia o permisos)
#         $3 = Directorio de Trabajo
#-----------------------------------------------------------------------
trataErrores()
{

  ERROR="1"

  case $1 in
     -ayuda) # Solicitud de ayuda
            ayuda
        exit $ERROR;;

     -tryMirror) 
        echo "===========> Trying $3 from Mirror: " $2
        echo;;

     -downloadSucceed) 
        echo
        echo "===========> Download succeed for $3 from " $2;;

     -downloadFailed) 
        echo
        echo "===========> $3 not found on mirror  " $2;;

     -noMirrors) # There is no mirrors for this package
    echo "ERROR ==> Package $2 has no mirror list"
         exit $ERROR;;


     -packageNotFound) # Package not found on any mirror
    echo "ERROR ==> Package $2 not found on any mirror of the list"
         exit $ERROR;;

  esac
}

################################################################################
# MODULE DOWNLOAD ====> FUNCTIONS FOR DOWNLOADING THE PACKAGES 
################################################################################

#-----------------------------------------------------------------------
#  DOWNLOAD PACKAGE 
#-----------------------------------------------------------------------
#   Try to download one package
#  from several mirrors. If all of them
#  fails, return 1
#
#   $1 = Number of tries per mirror
#   $2 = Package to download 
#   $3 ...  $N = List of mirrors
#-----------------------------------------------------------------------
downloadPackage () { 


   # 1.- Check that exist at least one Mirror on the input List
   #-----------------------------------------------------------
   if [ $# = 2 ]; then 
      trataErrores -noMirrors $2


   # 2.- Search for a the package on the mirrors list
   #-----------------------------------------------------------
   else

       POSITION=1
       for MIRROR in $@; do

          # 2.1.- Capture tries per mirror
          if [ $POSITION = 1 ]; then
               TRIES=$MIRROR

          # 2.2.- Capture package name
          elif [ $POSITION = 2 ]; then
               PACKAGE=$MIRROR

          # 2.3.- Try to get the package from current mirror
          else

                # Try the download
                trataErrores -tryMirror $MIRROR $PACKAGE
                `wget --tries=$TRIES $MIRROR$PACKAGE` 

                # Check if succeed
              if [ $? = $OK ]; then
                     trataErrores -downloadSucceed $MIRROR$PACKAGE $PACKAGE
                       break;
                     
              fi

                # Report the fail
        trataErrores -downloadFailed $MIRROR$PACKAGE $PACKAGE

          fi

          # 2.4.- Incrementing position
          POSITION=`expr $POSITION + 1`

       done 
   fi

   # 4.- Package not found of the list of mirrors
   #-----------------------------------------------------------
   if [ $POSITION = $# ] && [ $? != $OK ]; then
    trataErrores -packageNotFound $PACKAGE
   fi
}

#-----------------------------------------------------------------------
#  GET PACKAGES 
#-----------------------------------------------------------------------
#   Downloading the packages
# from the current mirror
#-----------------------------------------------------------------------
getPackages() {


        echo  "-------------------------------------------------------"
        echo  " DOWNLOADING REQUIRED PACKAGES "
        echo  "-------------------------------------------------------"
        echo

        # 1.- Check Kernel Version
        VERSION_1=`uname -r | awk 'BEGIN {FS=".";}{print $1}'`
        VERSION_2=`uname -r | awk 'BEGIN {FS=".";}{print $2}'`
        VERSION_3=`uname -r | awk 'BEGIN {FS=".";}{print $3}'`
        NEW_V=1;

        # 2.- Download the source code
        if   [ $VERSION_1 -gt 2 ] ; then # Kernel Over 2.***
	   NEW_V=1;
           downloadPackage 1 ${NEW[*]}
        elif [ $VERSION_1 -lt 2 ] ; then
           NEW_V=0;
	   downloadPackage 1 ${OLDER[*]}
	else
             if [ $VERSION_2 -lt 6 ] ; then # Kernel Over 2.11
                  NEW_V=0;
                  downloadPackage 1 ${OLDER[*]}
	     elif [ $VERSION_2 -gt 6 ] ; then
		  NEW_V=1;
                  downloadPackage 1 ${NEW[*]}
             else 
                 if [ $VERSION_3 -lt 11 ] ; then # Kernel Over 2.11
                     NEW_V=0;
                     downloadPackage 1 ${OLDER[*]}
	         elif [ $VERSION_3 -gt 11 ] ; then
                     NEW_V=1;
                     downloadPackage 1 ${NEW[*]}
                 else 
                     NEW_V=1;
		     downloadPackage 1 ${NEW[*]}
                 fi
             fi
         fi

        echo  "-------------------------------------------------------"
        echo  " UNPACK COMPILE AND INSTALL  ${WORK_DIR}/${NEW[0]}"
        echo  "-------------------------------------------------------"
        echo
        
        if [ $NEW_V -eq 1 ]; then
           tar xvzf ${WORK_DIR}/${NEW[0]} # Unpack
           cd ${WORK_DIR}/gspcav*
           make && make install 
           rm -R ${WORK_DIR}/gspcav*
        else
	   tar xvzf ${WORK_DIR}/${OLD[0]}
	   cd ${WORK_DIR}/spca5xx*
           make && make install
           rm -R ${WORK_DIR}/spca5xx*
        fi
        

 }

################################################################################
# MAIN
################################################################################
cd $WORK_DIR
getPackages




---

### Post by LostinSpacetime on 2008-01-25
Hello cesar_spain :)
I am looking for somebody who can help me and I believe U might be the right one. I have a (probably basic) question. First to my problem.
My webcam (Logitech Quickcam Messenger) works fine on my system (Ubuntu Feisty Fawn) and after using gstfakevideo, I can use it even in Skype. My problem, is that the picture is far to dark and the auto exposure doesn't work with the driver I have. It looks like the driver used is usbvideo, but I couldn't figure out how/if one can adjust the brightness with this driver. But I found out, that there is a far better driver for this webcam, namely the quickcam-usb driver. After downloading the source, and a "sudo make install" everything seemed to be ok. sudo modprobe quickcam did its job.
Now to my question. In my case I have (at least) two drivers which can handle the webcam. It looks like the device is still using the usbvideo driver. How can I change that???

Thanks in advance.

---

