# React-concepts

**difference between State and Props**:
**Props**: Props are objects that holds data which can be passed to a component. It is read only and contains the attributes of a tag and works similar to html attributes. It is similar to arguments of a function. it is immutable i.e. it cannot be modified inside a component.

**State**: State is an updatable stucture which contains data about the component and can change over time. It can change as a response to user action or system events. It can be modified inside the component or by the component directly. It represents information or state of a component.

**useState API**: useState is a hook, a hook is a special function which lets you "hook into" react features. useState hook lets you add react state to functional components. which basically means it lets you modify the local state of the component.

                                                   *****************************************

**Map**: It iterates over an array elements and returns a new array;

**Filter**: it iterates over an array elements and returns a new array with elements satisfying a condition which is given. It works basically as a filter as the name suggests.

**Reduce**: It reduces an array to a single value by iterating over an array, it returns the value of the callback function, the value is stored in accumulator.

                                                   ******************************************
 **Implementation of Map,Filter and Reduce**

```
function MyArray() {
    this.length = 0;
    Object.defineProperty(this,"length", {
        value: 0,
        enumerable : false,
        writable : true
    })
}

MyArray.prototype.push= function(el) {
  this[this.length] = el;
  this.length++;
}

MyArray.prototype.pop = function(el) {
  this.length--;
  delete this.length;
}

MyArray.prototype.map = function(cb){
    let result = new MyArray();
    for(const index in this) {
        if(this.hasOwnProperty(index)) {
            result.push(cb(this[index],index,this));
        }
    }
        return result;
}

MyArray.prototype.filter = function(cb) {
    let result = new Array();

    for(const index in this) {
      if(this.hasOwnProperty(index)){
        if(cb(this[index],index,this)) result.push(this[index]);
    }
    }
    return result;
}

MyArray.prototype.reduce = function(cb,initialValue = null) {
    let accumulator = initialValue;

    for(const index in this) {
        if(this.hasOwnProperty(index)) {
          accumulator = cb(accumulator,this[index],index,this)
        }
    }
  return accumulator;
}

let arr = new MyArray();

arr.push(1);
arr.push(2);
arr.push(3);
arr.push(4);
arr.push(5);

console.log(arr);

let x = arr.reduce((acc,i)=> acc+i,10);
console.log(x);
```
