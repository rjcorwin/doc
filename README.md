**CURRENT DEVELOPMENT TEAM**: [BENJAMIN SHUTE](http://www.farmhack.net/users/brshute), [RJ STEINERT](http://farmhack.net/users/rjsteinert-0), [LOUIS THIERY](http://www.louisthiery.com)

## Goals of this project
We will create and field test a farmer-built electronic tool that can monitor greenhouse temperature, record greenhouse data, and alert the farmer to problems in the greenhouse via cell phone text message. This tool will be much more affordable and useful than commercially available greenhouse alarms (which rely on landline connections or internet connections, which usually aren’t available in the greenhouse). The tool will be created through a partnership between a farm and two consultants with expertise in electronics development and software programming. Once developed, the tool will be field tested by several farmers, to ensure that it is accessible and appropriate for various operations. Once we’ve got it right, we will do outreach to ensure that many other farmers can benefit from this useful and economical tool. The project will also leave open possibilities for future developments: while this tool will be simple, straightforward and approachable for farmers, it will also be flexible and robust enough that more technically inclined farmers could add features to it for greater functionality, such as turning on or off greenhouse fans, monitoring soil moisture and humidity, or monitoring produce storage facilities.

Bill of Materials:
| Item | Cost |
| ------------- | ------------- |
| [Arduino UNO](https://www.adafruit.com/products/50)  | $30 |
| [Datalogging Shield](https://www.adafruit.com/products/243) | $20 |
| [10K Precision Epoxy Thermistor](https://www.adafruit.com/products/372) |$4|
|SD Card 1GB or more|$2|
| Enclosure | $12|
| [9V Power Supply](https://www.adafruit.com/products/63) | $6 |
|**Phone Related**| |
| [Motorola C168i](http://www.ebay.com/ctg/Motorola-C168I-ATT-Cellular-Phone-/99980032?_refkw=motorola+c168i&_pcatid=801&rt=nc&_pcategid=9355&_pdpal=1&_dmpt=Cell_Phones) + SIM Card | $30  |
| [3/32 Minijack](http://www.radioshack.com/product/index.jsp?productId=2104064) | $4 |
| Logic Shifter | $1|
|**Back-up Battery**| |
| [Backup 9V Adapter](https://www.adafruit.com/products/67) | $6 |
|[2 Diodes](https://www.adafruit.com/products/755)|$1.50|
|[2 DC barrel jacks](https://www.adafruit.com/products/373)|$2|

##How to Build (v0.25)##

###Preparation###

1. Download [Arduino IDE v1.0](http://arduino.cc/hu/Main/Software) and the libraries that we will need:
   * [Fido library](https://github.com/lthiery/Fido) 
   * [SD](https://github.com/adafruit/SD) (replace the default one) and [RTC](https://github.com/adafruit/RTClib) library from Adafruit
   * [GSMSerial](https://github.com/lthiery/GSMSerial) library
   Some of these libraries are still getting tweaked quite often, but once we have some stable versions we'll offer a single zip file download for all of them

    An IDE is an "Integrated Development Environment," or in plain english, it has everything you need to program your Arduino. The full tutorial is available on the [Arduino site](http://arduino.cc/en/Guide/Environment) but here is a quick conceptual summary.

    In this environment, you will be writing code in C++. There is an upload button which automatically "compiles" your code (turns it into processor code) and then uploads it to your Arduino. If you are working on your code for a while, it is helpful to compile it periodically to catch syntax errors as you make them. If all this is overwhelming, don't worry. You don't need to write any code for this project and all you *have* to do is learn how to upload code! 

    Your IDE also keeps all your "libraries" in order. Libraries are pieces of already written code that you can call on when writing your Arduino program. They are usually device specific, so for example, with Fido we use a library that was specially written for a cell phone and another for the data logging shield. These are all kept in the libraries folder (not to be confused with lib) in the Arduino file and your Arduino IDE discovers them each time you launch it. You'll need to put the libraries in the downloadable zip file in your Arduino folder.

    Finally, before your IDE will be able to see your Arduino, make sure your computer recognizes it! There are device drivers included in the Arduion folder and if you have trouble, refer to the [Arduino web site](http://arduino.cc/en/Guide/HomePage).

2. Activate SIM card and load with text messages

    We are using the Motorola C168i because of the 3/32 stereo jack connection - it's really easy to make the Arduino interface with it but sadly most modern cell phone don't use that kind of connection anymore.

    You will need a SIM card for your C168i if you don't yet have one. Unless you specifically sought out an unlocked one, your phone will most likely be locked to the AT&T network and you will need one of their SIM cards which can be purchased on [their site](http://www.wireless.att.com/cell-phone-service/cell-phone-details/index.jsp?device=AT&q_sku=sku981990&WT.srch=1#fbid=W59whJKfMDW). You may also be able to find one in their stores (to be confirmed) and you can definitely find them at Radioshack (just buy their cheapest Go Phone and it will be included). When activating it, I recommend the 10c/min plan, and that you simply buy text message packages that are valid for 30 days ($5 for 200, $10 for 1000).

    Also, since we will be leaving our cell phone charging most of the time, you'll benefit from going into the settings and silencing the phone so as not to get beeped at every few minutes. 

###Build###
1. Assemble Adafruit data logging shield following [their easy tutorial](http://www.ladyada.net/make/logshield/make.html)
    Notes: 
        1. If you don't have a vise, laying the board down [on some bricks](http://www.farmhack.net/sites/default/files/IMG_1237.JPG) or anything other similar setup should do the trick
        2. You do *not* need to solder the RTC clock mount if you don't want to
        3. You should wire a jumper between pins 2 and 3 and the LED holes right next to them if you want them to blink (I recommend clippings from the legs of a diode to do so)
<a href="http://louisthiery.com/wp-content/uploads/2012/05/IMG_1269.jpg"><img src="http://louisthiery.com/wp-content/uploads/2012/05/IMG_1269-150x150.jpg" alt="" title="IMG_1269" width="150" height="150" class="alignright size-thumbnail wp-image-153" /></a>

2. [Make the wire](http://www.farmhack.net/wiki/cellphone-arduino) to connect your cell phone to your Arduino

3. [Connect the cell phone and thermistor to shield](http://www.farmhack.net/wiki/building-shield)

4. Build your [back-up battery](http://www.farmhack.net/wiki/back-battery-arduino)

5. Upload the Fido sketch to the shield and [program via text message](http://www.farmhack.net/wiki/program-fido)!

##Documentation To-Do##
<del>1. Why the phone and how to get a SIM card (10c/min), silencing phone</del>
<del>2. Make little changes to Adafruit tutorial: jumper LED's, RTC clock without mount</del> wrote notes instead
<del>3. Explain Integrated Development Environment, Arduino drivers, and how to install libraries</del>
4. Temperature sensor intro (-55-105C)
<del>5. Include picture for build step 1, note 1</del>
6. Ammend wire tutorial to include logic shifter instead of voltage divider