# ReplicaSera Compatability

this fork adds compatibility with sera and replica specifically for your writelib module.

original implementation:

```lua
WriteLib.AddMoney = function( replica, amount )
    local NewAmount = math.max(0, replica.Data.Money + amount)
    replica:Set({ "Money" }, NewAmount)
    return NewAmount
end

```

new implementatiion:

```lua
WriteLib.AddMoney = {
	Schema = Sera.Schema({
		Amount = Sera.Uint32,
	}),
	Fn = function( replica, args )
		local NewAmount = math.max(0, replica.Data.Money + args.Amount)
		replica:Set({ "Money" }, NewAmount)
		return NewAmount
	end,
}

```

todo: add more stuff idk
