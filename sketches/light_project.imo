/**
* Pin Cycle LED using analog with PWM.
* - 3 RGB LEDs
* - 1 Photocell that activates lights
*/
// RED PINS
const int redPin1 = 3;
const int redPin2 = 4;
const int redPin3 = 5;

// GREEN PINS
const int greenPin1 = 6;
const int greenPin2 = 9;
const int greenPin3 = 10;

// BLUE PINS
const int bluePin1 = 20;
const int bluePin2 = 21;
const int bluePin3 = 22;

// PHOTOCELL (works with a0 usually)
const int photocellPin = 14;     

// LED OFF
const unsigned int off = 0;
unsigned int rgbValues[4];

void setup() {
  applyRGBValues(0,0,0);
}

void loop() {
  // Choose the led colors to cycle between.  
  rgbValues[0] = 255;
  rgbValues[1] = off;
  rgbValues[2] = off;

  for (int decrementer = 0; decrementer < 3; decrementer += 1) {
    crossFadeLED(decrementer);
  }
}

/** 
 *  Cross-fade between colors
 */
void crossFadeLED( unsigned int decrementer ){
    int incrementor = decrementer == 2 ? 0 : decrementer + 1;
    for(int i = 0; i < 255; i += 1) {
      rgbValues[decrementer] -= 1;
      rgbValues[incrementor] += 1;
      if ( isDark() ){
        applyRGBValues(rgbValues[0], rgbValues[1], rgbValues[2]);
      } else {
        applyRGBValues(off, off, off);
      }
      delay(5);
    }
}

boolean isDark()
{
  return (analogRead(photocellPin) < 40);
}

/**
 * Set LED Values
 */
void applyRGBValues(unsigned int red, unsigned int green, unsigned int blue) {
  analogWrite(redPin1, red);
  analogWrite(redPin2, red);
  analogWrite(redPin3, red);

  analogWrite(greenPin1, green);
  analogWrite(greenPin2, green);
  analogWrite(greenPin3, green);
  
  analogWrite(bluePin1, blue);
  analogWrite(bluePin2, blue);
  analogWrite(bluePin3, blue);
 }
