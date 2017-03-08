# NSA3xx-usb-recovery-stick
**Observations:**
- *ras.bin image files in the source tree are just placeholders*
- *real binary ras.bin files will only be published in release packages for each supported device*
- __*Release section is [here](https://github.com/vch42/NSA3xx-usb-recovery-stick/releases)*__

## About
With "create_usb" script you can easily create a recovery USB stick for the following Zyxel NAS boxes:
* NSA310
* NSA310s
* NSA320
* NSA320s
* NSA325

It is highly recomended to have console access to your NSA box during modding operations, or recovery ones, for that matter, in order to see any error messages that may appear.
**Console access equals easyer debugging.**

## How to use
### Using the *create_usb* script provided:
1. From the [release section](https://github.com/vch42/NSA3xx-usb-recovery-stick/releases), download the apropriate archive for the device you want to restore.
2. Unpack the archive on a linux box (tested on Debian 8) and enter the directory created.
3. Make sure you have a USB drive handy, formatted preferably as fat32.
4. Connect the USB drive to the linux box and see what device name gets assigned to it. `eg. /dev/sdd`
5. (Recomended) If you want, find your NAS box original MAC address. `eg. 00:48:78:AC:8B:9F`
5. As root, run `./create_usb <usb_device_name> [mac_address]`
   
   For example: `./create_usb /dev/sdd 00:48:78:AC:8B:9F`
6. Remove drive and connect it to the NSA box and power it up.
7. Wait until NSA powers down, then remove USB drive.
  - remove all cables for ~30sec
  - reconnect cables
  - power NSA up and test if the recovery succeded.
  
Obs.: *you can ommit the MAC address, in this case the default of 00:19:CB:00:51:81 will be setup after recovery*

### Manual stick creation
1. From the [release section](https://github.com/vch42/NSA3xx-usb-recovery-stick/releases), download the apropriate archive for the device you want to restore.
2. Unpack the archive.
3. Make sure you have a USB drive handy, formatted preferably as fat32.
4. Copy the entire content of the `content` directory directly into the USB drive root.
5. If you want to set the correct MAC address of your box, edit the file `nsa310_fw/usb_key_func.sh.2`.

   The line you have to change is `${USB_FW_PATH}/mrd_mac 00 19 CB 00 51 81`
   
   Replace `00 19 CB 00 51 81` with your MAC address.
   
   From the example above: `${USB_FW_PATH}/mrd_mac 00 48 78 AC 8B 9F`
6. Remove drive and connect it to the NSA box and power it up.

7. Wait until NSA powers down, then remove USB drive.
  - remove all cables for ~30sec
  - reconnect cables
  - power NSA up and test if the recovery succeded.

Obs.: *you can ommit the MAC address change, in this case the default of 00:19:CB:00:51:81 will be setup after recovery*
