# 05.04.1331Joystick
void setup() {
Serial.begin(9600);
pinMode(9,OUTPUT);//IN1
pinMode(10,OUTPUT);//IN2
}

void loop() {
int vrx,vry,sw;
int x;
vrx = analogRead(A0);
vry = analogRead(A3);
sw = analogRead(A4);

char buf[100];
sprintf(buf, "VRx=%d, VRy=%d, SW=%d" ,vrx,vry,sw);
Serial.println(buf);
x = map(vrx,0,1023,-255,255);
if (x > 0)
{
  analogWrite(9,x);
  analogWrite(10,0);
}
else
{
  analogWrite(9,0);
  analogWrite(10,abs(x));
}
}
